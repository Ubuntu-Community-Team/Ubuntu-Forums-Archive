---
title: "i am having a problem installing vmtool 6.0.0-45731 on my ubuntu guest OS"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by nwaice242 on 2007-10-19
this is where i have got to and i can't continue i don't know what to do again.please someone should help me.this is my third day trying to install vmtools 6.0.0


daniel@daniel-desktop:~/Desktop/vmware-tools-distrib$ sudo ~/Desktop/vmware-tools-distrib/vmware-install.pl
Password:
Creating a new VMware Tools installer database using the tar4 format.

Installing VMware Tools.  This may take from several minutes to over an hour
depending upon its size.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/usr/sbin]

In which directory do you want to install the library files?
[/usr/lib/vmware-tools]

The path "/usr/lib/vmware-tools" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware-tools]

The path "/usr/share/doc/vmware-tools" does not exist currently. This program
is going to create it, including needed parent directories. Is this what you
want? [yes]

The installation of VMware Tools 6.0.0 build-45731 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want
this program to invoke the command for you now? [yes]


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
Trying to find a suitable vmmemctl module for your running kernel.

None of the pre-built vmmemctl modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmmemctl module
for your system (you need to have a C compiler installed on your system)?
[yes]

Setup is unable to find the "make" program on your machine.  Please make sure
it is installed.  Do you want to specify the location of this program by hand?
[yes]

What is the location of the "make" program on your
machine?

The answer "" is invalid.  It must be the complete name of a binary file.

What is the location of the "make" program on your
machine?

please help me

---

### Post by Tex-Twil on 2007-10-20
Hi,
you have to install a compiler I guess. Try this

```

sudo aptitude install build-essential 

```

it should help.

cheers

---

