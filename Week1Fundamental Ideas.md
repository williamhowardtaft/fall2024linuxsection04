
Big Picture.

Before diving in Linux, we need to discuss couple of things, or try to understand
why exactly things, happens to be end up like that.

# === > Typical Computer System Architecture

* Physical Level -Computing machine (CPU,RAM,Memory,Devices)
* OS Level - Kernell(Mother of all programs, which controls who can access what), other programs refered usually as processes(or daemons)
* Program(Process,Job) - some program which can be written by person, which performs his own specific logic tailored to specific task
* End-User - person who communicates with program to accomplish task.


# === > Couple of words regarding OS (operating systems)

So since, hardware is a commodity or different component and more or less the same,
concentration happened on Operating Systems.
Because it is the first and main program which controls resources in your compute system.

Here story goes as next, before the dawn there was a Unix OS, mainly used for big servers, which costs millions of dollars.
Since it was the begining of computing era, it was simple as powerful calculators, so it had many security flaws, but overall was better than nothing and the main way of communcating was through punch cards and text.
(when I was a kid, my house was full of useless punch cards)

So since it was geared towards academic, governmental, and large corporate settings rather than personal computing.

It was assumed to be okay.Because it's not like everybody has access to it, so assumption was that if person want to use it, he can manage to learn a couple of text commands :)

So next step was kind of controversial. Unix was kind of open source. And when you have many people working together, and nobody get paids and everything works on enthusiasm, there were some contradiction.

So one group of programmers, said we gonna create our own OS.

By that, we end up having Linux and MacOS family.

After that MacOS, kind of consolidated, Apple has tight control over macOS, both in terms of software and the hardware it runs on. This makes macOS a more consolidated ecosystem, without the fragmentation observed in Linux.

but Linux went in different direction, from time to time some group of people say, we want to have our own version of Linux and they started to create different versions or distros.

The important thing to understand, is that in essence most of them still use a Kernel created by Linux Torvalds. It's the "glue" that holds everything together, and its development still is overseen by Linus Torvalds and a team of contributors.

# ===> GUI or not GUI
As modern computers become widespread, people realize that not that everybody wants to be able to communicate with computer system, only through keyboard and terminal, they said let's make them more accessible all general principles are written on the stone but in addition to text based control over OS, we will provide another channel to communicate based on Graphical Interface + Mouse.
in that regard Windows OS is famous example.

GUI in Other Operating Systems
While Windows made GUI mainstream in the PC world, Apple's Mac OS was also instrumental in popularizing the graphical interface, even inspiring some of Windows' design. Linux, which started as a command-line interface OS, now also has various distributions that offer sophisticated graphical interfaces like GNOME, KDE, and others.

# => Back to Class Philosophy.

Since you are future software engineers at Google, Amazon and Apple.
We need to stick with text-based interfaces, because despite the ubiquity of GUIs, text-based interfaces haven't disappeared. Many system administrators, programmers, and power users still prefer using the command line for certain tasks because it can be more efficient and allows for a high degree of automation

Understanding and mastering text-based interfaces is considered a fundamental skill for several reasons:

Efficiency
Text-based interfaces are often faster for certain tasks, especially when those tasks are complex and require multiple steps that can be scripted or automated.

Scripting and Automation
The command line makes it easier to create scripts that can automate a range of tasks, from simple file operations to complex deployment workflows. This is invaluable in a professional setting.

Resource Usage
Text-based interfaces generally use fewer system resources than GUIs, which is particularly important for remote connections or when working with high-performance computing systems.

Versatility
Knowing how to use a text-based interface opens up a wide range of tools and utilities that simply are not available through a GUI.

Deeper Understanding
Using text-based interfaces often forces one to have a better understanding of the system's underlying operations. This can be invaluable for debugging and troubleshooting.

Industry Expectations
Many of the tools used in DevOps, backend development, data engineering, and other specialized roles are optimized for command-line use. 


# => Environment:
Each of you gonna have 
Remote Virtual Machine in Azure:

Defaults: If you change it, make sure to save your credentials. We will not be able to recover it.
User: student
Password: UTRGVstudent1
      
VirtualBox with Ubuntu: As a backup, we recommend setting up a local VirtualBox instance running Ubuntu on your personal computer. This will serve as an alternative development environment should there be issues with Azure connectivity.

Free Cloud Accounts: Students have the option to create free accounts on Azure, AWS, and Google Cloud to follow along with the class activities and assignments involving virtual machines

# => Typical Workflow Example +  Fundamental to understanding how to interact effectively with a Linux-like shell.

Pre-requisites

Before starting, make sure you have g++ installed on your Ubuntu system. If it's not installed, you can install it by running the following command:

sudo apt update
sudo apt install build-essential

The command sudo apt install <package-name> is commonly used on Debian-based Linux distributions like Ubuntu to install software packages. Let's break down what each part does:

sudo: Stands for "superuser do." This command allows you to run other commands with administrative (superuser) permissions. Essentially, it lets you execute a command as the root user.

apt: Short for "Advanced Package Tool." This is the package management system used by Debian and its derivatives like Ubuntu. It allows you to install, update, and remove software packages.

install: This is the command that tells apt what you want to do—in this case, install a new package.

<package-name>: This is the name of the package you want to install. Replace <package-name> with the actual package name. For example, sudo apt install tree would install the tree package.

So, when you run sudo apt install build-essential, you are asking the system to use administrative permissions to install the build-essential package. The build-essential package includes a bunch of development tools, like compilers and libraries, that are commonly used for building software on Ubuntu systems.


# Version 1: Simple Hello World Program
Create the File: Open your terminal and type the following command to create a new C++ file:

touch hello.cpp

Edit the File: Open the file using a text editor like nano or vim. 
For this example, we'll use nano:

nano hello.cpp

Add Code: Enter the following C++ code to print "Hello, world!":

#include <iostream>

int main() {
    std::cout << "Hello, world!" << std::endl;
    return 0;
}

Save the file and exit the editor.

Compile the Code: Compile the C++ code using g++:

g++ hello.cpp -o hello

Run the Program: After compilation, run the program:

./hello
You should see Hello, world! printed on the terminal.

# Version 2: Accepts Name as Argument
Modify your hello.cpp to look like this:

#include <iostream>

int main(int argc, char *argv[]) {
    if (argc > 1) {
        std::cout << "Hello, " << argv[1] << "!" << std::endl;
    } else {
        std::cout << "Hello, world!" << std::endl;
    }
    return 0;
}
Compile and run it as before. You can now run it with a name argument:

./hello Alice

This should print Hello, Alice!.

# Version 3: Optional Flag for Capitalization
Modify your hello.cpp to look like this:

#include <iostream>
#include <string>
#include <algorithm>

int main(int argc, char *argv[]) {
    std::string greeting = "Hello, world!";
    
    if (argc > 1) {
        greeting = "Hello, " + std::string(argv[1]) + "!";
    }

    if (argc > 2 && std::string(argv[2]) == "--capitalize") {
        std::transform(greeting.begin(), greeting.end(), greeting.begin(), ::toupper);
    }

    std::cout << greeting << std::endl;

    return 0;
}

Compile and run as before:
g++ hello.cpp -o hello
./hello Alice --capitalize

This should print HELLO, ALICE!.

=> Most critical Point to observe:
Understanding this will make you life much more easier

In Unix-like operating systems such as Linux, the shell is essentially a user interface for running programs. Most of these programs are often small utilities written in C or other languages, each designed to do a specific task very well. (there are like 1000+ programs)

* Command Line Syntax
When you type a command in the shell, the typical syntax is:

command [arguments] [options/flags]

Command: This is usually the name of the program you want to run.
Arguments: These are positional parameters that the command needs to execute.
Options/Flags: These are optional and are used to modify the behavior of the command. They usually start with a hyphen.


# C++ example beautifully mirrors this structure:

Command: When you run ./hello, ./hello is the command you're executing, similar to commands like ls.

Arguments: Alice in ./hello Alice is an argument, just like the filenames you would provide to a command like cp.

Options/Flags: --capitalize in ./hello Alice --capitalize is an optional flag that modifies how the command behaves.

Understanding this structure is fundamental to understanding how to interact effectively with a Unix-like shell, and your C++ program serves as a wonderful hands-on example to illustrate these concepts.

# Basically that's it that's whole Linux programming in essence :)

I am joking, but it's no far from the truth.

So for the rest of semester we are going to explore and practice most commands(programs) and patterns which you most likely you are going to encounter in future jobs.

=> Let's start with basics
Most useful commands is about a navigation:

# Basic Navigation Commands
=> pwd: Print Working Directory
Shows the full pathname of the current working directory.
pwd

=> ls: List
Lists all the files and directories in the current directory.
ls

=> cd: Change Directory

Changes the current directory to the one specified in the arguments.
cd /path/to/directory

=> mkdir: Make Directory

Creates a new directory.
mkdir new_directory

=> rmdir: Remove Directory
Removes an empty directory.

rmdir directory_name

# File Manipulation Commands
=> touch: Create File

Creates a new empty file.

touch new_file.txt

=> rm: Remove File
Deletes a file. Use cautiously.
rm file_name
=> cp: Copy
Copies files or directories.

cp source destination

=> mv: Move

Moves files or directories, can also be used to rename files.
mv old_name new_name



Most famous command, because joke says: go to read manual page
=> man: Manual
Displays the user manual for the specified command.

man command_name



These commands offer the basic functionalities you'd need to navigate and manipulate a Linux filesystem. They are the building blocks for many more complex operations and scripts.


# Assignment: Create a Simple File and Folder Structure and Verify Using tree

Objectives
Create a directory structure that includes a couple of sub-directories.
Create some files within these directories.
Use the tree command to verify your work.
Steps

Open a terminal.

Create a root directory for your assignment and navigate into it:
mkdir AssignmentRoot
cd AssignmentRoot

Create two sub-directories within AssignmentRoot:
mkdir SubDir1 SubDir2

Navigate into SubDir1 and create a file:
cd SubDir1
touch file1.txt
cd ..

Navigate into SubDir2 and create another file:

cd SubDir2
touch file2.txt
cd ..


Display the tree structure listing of AssignmentRoot and its contents:

tree AssignmentRoot

Note: If the tree command is not installed, you can install it using:

sudo apt install tree

The tree command will display a hierarchical structure of directories and files, giving you a clear view of the structure you've just created.

After completing these steps, you should see an output that confirms you've created AssignmentRoot, with two sub-directories SubDir1 and SubDir2, each containing a text file (file1.txt and file2.txt, respectively). This verifies that you've correctly followed the assignment steps.


If you don't want to install tree, you can use the built-in find command to display the directory structure, although it won't be as neatly formatted as with tree.

From within the AssignmentRoot directory, you can use:

find .

This will list all files and directories under the current directory, which in this case is AssignmentRoot.
