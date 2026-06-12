---
title: "Linux Questions (Genral)"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by kris_sti on 2007-01-08
Hi Guys I'm a student and I'm having a hard time mastering linux and thats what all the computers run. I have a worksheet and i was wondering if anyone could answer some questions for me, thanks: 




1.	The _____ directory is the b eginning of the Linux directory structure.
a./
b./root
c.home
d./dev/had
e.

2. 	The pwd command is used to:
a.Process writeable domains on the network
b.Control power used by a Linux system
c.Print the current working directory to the screen
d.Print a summary of the writeable devices on the system

3.	As with a DOS system the command cd.. can be used to change to the parent directory at any time. True or False?

4.	Name three commands that can be used to view the contents of text files.

5.	The command Ls -l is invalid because:
a.	Linux commands cannot contain hyphens
b.	Linux commands are case sensitive
c.	The ls command is not a real command
d.	The -l option is not supported by the ls command

6.	The command chmod 652 test grants ___ execute permission to the test file.
a.	user
b.	group
c.	other
d.	all users on the system

7.	The owner and group assigned to a file are shown by which of the following commands?
a.	chown
b.	ls -l
c.	modprobe
d.	useradd

8.	Execute permission on a file is required to
a.Launch that file as a program
b.Create a directory with a matching name
c.Allow other users to read the file
d.Use the insmod command to add the file as a module

9.	Describe the purpose of function libraries and name two directories where they are commonly located.

10.	The command rpm -q packagename does the following:
a.Determines whether packagename is installed on the system
b.Locates packagename on a CDROM
c.Erases packagename if it is currently installed
d.Summarizes the disk quota for users of packagename.

11.	The tar command creates archive files that are commonly compressed by the ___ command.
a.	bzip
b.	compress
c.	zip
d.	gzip

12. 	Contrast the advantages of rpm and tar formats.
.
     13.	Which of the following represents a development release of the Linux kernel?
a.1.2.13
b.2.1.42
c.2.0.10
d.2.2.5

14.	Name two methods of determining the version and timestamp of the kernel currently running on a Linux system.

15	The module files loaded by the insmod command are located in a subdirectory of /etc/modules. True or False?

16.	Red Hat Linux uses a program called ______ to automate loading of kernel modules as they are needed.
a.modprobe
b.kerneld
c.find
d./lib/modules

17.	Name four commands used to work with kernel modules.

Any of these would be appropriate:
- insmod
- modprobe
- lsmod
- rmmod
- kerneld (less appropriate as a response because it is a daemon rather than a system administration command)

18.	The terms module parameter and boot parameter refer to the same basic thing. True or False?

19.	The process of recompiling the Linux kernel does not include:
a.Creating a configuration file
b.Making certain the kernel source code is installed
c.Running the make command
d.Inserting kernel modules that provide support for recompiling the kernel


20.	After creating a new kernel file you must reconfigure LILO so that:
a.The new kernel can be started by the LILO program when the system is rebooted
b.The older kernel version is gracefully unloaded from memory
c.Existing kernel modules do not cause a memory conflict when loaded
d.Security enhancements remain in force

21.	The _____ program displays kernel hardware configuration messages from the system boot-up.
a.init
b.chmod
c.dmesg
d.uname

22.	Why is modprobe preferred over insmod as a tool for added modules to the kernel?

23.	The init program uses the following configuration file:
a./etc/lilo.conf
b./etc/inittab
c./etc/modules/inittab
d./etc/rc.d/rc

24.	Name the two runlevels normally used to run a Linux-based computer and describe the difference between those two runlevels.

25.	Files in the runlevel subdirectories, such as /etc/rc.d/rc3.d, are actually pointers to scripts in /etc/rc.d/init.d. True or False?

26.	The files in /etc/rc.d/init.d can be used to:
a.Automatically insert kernel modules
b.Stop and restart most standard services in Linux
c.Reconfigure the LILO program after recompiling the kernel
d.Set default file permissions for the root user

27.	The scripts in /etc/rc.d/init.d are provided by:
a.The system administrator who installs Linux
b.The rc script, which runs before any of the init.d scripts
c.The rpm that installs the service that the script controls
d.The kernel itself

28.	The configuration data stored in files within the /etc/sysconfig directory can be modified using many different configuration utilities. True or False?

29.	Name three commands that can be used to begin a graceful shutdown of Linux.

30. Describe why the LILO program must be executed after making changes to the lilo.conf file.


I know it's long but if you guys can at least help me understand some of these questions.

---

### Post by taurus on 2007-01-08
Is this a homework assignment for a computer class or something???

---

### Post by jdong on 2007-01-08
Many of these are quite simple questions that can be answered from a simple google/wikipedia search.

This is not a homework help forum; if you've made decent effort at attempting the assignment and had a few specific questions that you'd wanted to ask, that'd be a different situation.

---

