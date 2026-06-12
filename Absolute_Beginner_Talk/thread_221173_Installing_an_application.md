---
title: "Installing an application"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by dcmax on 2006-07-22
Folks, I have Ubuntu 6.06 installed on top of Windows XP Pro, thanks to VMware 5.5.  I am trying to install VMware Tools.

[I]The instructions provided say, "To install/upgrade VMware Tools for Linux, run the program "vmware-install.pl" from a command prompt, either in text mode or from a terminal inside an X session.  You must have super user privileges (i.e. be logged as root) to run it).

     ./wmware-install.pl[/I]

I gather Ubuntu is running X, so my challenge is to get to "Terminal" which I find under Application : Accessories.

The folder that contains uncompressed VMware software I am trying to install is on my desktop in a folder called, "vmware-tools-distrib". 

I cannot figure out how to change directories to that folder in order to execute the installation.

I tried typing "cd vmware-tools-distrib" but that did not work.

Any suggestions?  Sorry for being such a lame noob! :-| 

Max

---

### Post by taurus on 2006-07-22
Try

```

cd ~/Desktop/vmware-tools-distrib

```

---

### Post by jimmygoon on 2006-07-22
> **dcmax said:**
> Folks, I have Ubuntu 6.06 installed on top of Windows XP Pro, thanks to VMware 5.5.  I am trying to install VMware Tools.

[I]The instructions provided say, "To install/upgrade VMware Tools for Linux, run the program "vmware-install.pl" from a command prompt, either in text mode or from a terminal inside an X session.  You must have super user privileges (i.e. be logged as root) to run it).

     ./wmware-install.pl[/I]

I gather Ubuntu is running X, so my challenge is to get to "Terminal" which I find under Application : Accessories.

The folder that contains uncompressed VMware software I am trying to install is on my desktop in a folder called, "vmware-tools-distrib". 

I cannot figure out how to change directories to that folder in order to execute the installation.

I tried typing "cd vmware-tools-distrib" but that did not work.

Any suggestions?  Sorry for being such a lame noob! :-| 

Max

Your problem is that you were starting in your user directory and trying to access a folder on the Desktop... Look:

/home/USERNAME/Desktop/vmware-blabla

your terminal was in /home/USERNAME

so you should have done

"cd Desktop"
"cd vmware-blabla"

---

### Post by dcmax on 2006-07-22
Thank you kindly, that worked. 

However, now that I have tried to execute the .pl file, Ubuntu says to me:

*"Please re-run this program as the super user. Execution aborted."*

I installed Ubuntu myself.  I created only one username and PW.  How is it that I lack these privileges myself?  How do I log in as the "super user," or otherwise change my perms so I can install this app?

---

### Post by taurus on 2006-07-22
```

sudo ./wmware-install.pl
(and use the same password that you log in...)

```

---

### Post by dcmax on 2006-07-22
Okay, thanks again, that worked.  However, I am stuck again!  :-k 

I am able to start the installation, but apparently the program needs to find a file called "Make" that it cannot find in order to complete the installation.  Any idea what I need to do?  Below is a screen text copy/paste....

[I]
Creating a new installer database using the tar3 format.

Installing the content of the package.

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

The path "/usr/lib/vmware-tools" does not exist currently. This program is goingto create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware-tools]

The path "/usr/share/doc/vmware-tools" does not exist currently. This program isgoing to create it, including needed parent directories. Is this what you want?
[yes]

The installation of VMware Tools 5.0.0 build-13124 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want
this program to invoke the command for you now? [yes]


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes]

Setup is unable to find the "make" program on your machine.  Please make sure itis installed.  Do you want to specify the location of this program by hand?
[yes]

What is the location of the "make" program on your machine?[/I]

---

### Post by taurus on 2006-07-22
```

sudo apt-get install build-essential
sudo /usr/bin/vmware-config-tools.pl

```

---

### Post by dcmax on 2006-07-22
Ok, the process started to download files:

*[Connecting to us.archive.ubuntu.com (146.137.96.7)]*

However, after 11% it hung.  I closed terminal, restarted the download, and it hangs at 0%.  

I rebooted my computer, started terminal, and re-tried. Same result: stuck at 0%.

Is there an alternate download source that can be specified?

---

### Post by jimmygoon on 2006-07-22
> **dcmax said:**
> Ok, the process started to download files:

*[Connecting to us.archive.ubuntu.com (146.137.96.7)]*

However, after 11% it hung.  I closed terminal, restarted the download, and it hangs at 0%.  

I rebooted my computer, started terminal, and re-tried. Same result: stuck at 0%.

Is there an alternate download source that can be specified?

"sudo gedit /etc/apt/sources.list"
"Search -> Replace"

"us." with "" (us. with [blank]

That way it removes us. from your repository listing and just uses the almighty ubuntu servers... also for the rest of your vmware-config.pl... you are going to end up needing some other stuff too I bet... in which case I will point you to the thread that I made aw... about 6 months ago in which I was doing the same thing as you... lemme find it


[http://ubuntuforums.org/showthread.php?t=82666](http://ubuntuforums.org/showthread.php?t=82666)

---

### Post by taurus on 2006-07-22
You need to edit your /etc/apt/sources.list and remove the "us" in front of the lines since us.archive.ubuntu.com is currently down!  It has been reported many times today about the problem with us.archive.ubuntu.com.  Maybe it's down for some loving!!!

```

sudo gedit /etc/apt/sources.list

```
Then, update it and install it again.

```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by dcmax on 2006-07-22
Okay, I am not sure if WMware Tools is actually installed correctly, but I was able to launch it after I did the following:

[I]myusername@myusername-desktop:~$ CC="/usr/bin/gcc-3.4" sudo /usr/bin/vmware-config-tools.pl
Password:

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:                                      done
Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc-3.4". Use environment variable CC to override.

Your kernel was built with "gcc" version "4.0.3", while you are trying to use
"/usr/bin/gcc-3.4" version "3.4.6". This configuration is not supported and
VMware Tools cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc-3.4" version "3.4.6", or restart
/usr/bin/vmware-config-tools.pl with CC environment variable pointing to the
"gcc" version "4.0.3".

The filesystem driver (vmhgfs module) is used only for the shared folder
feature. The rest of the software provided by VMware Tools is designed to work
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine.
These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

Trying to find a suitable vmxnet module for your running kernel.

None of the pre-built vmxnet modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmxnet module for
your system (you need to have a C compiler installed on your system)? [no]

The fast network device driver (vmxnet module) is used only for our fast
networking interface. The rest of the software provided by VMware Tools is
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils,
make and the kernel sources for your running kernel are installed on your
machine. These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

No X install found.

Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   DMA setup:                                                          done
   Guest operating system daemon:                                      done

The configuration of VMware Tools 5.0.0 build-13124 for Linux for this running
kernel completed successfully.

You must restart your X session before any mouse or graphics changes take
effect.

You can now run VMware Tools by invoking the following command:
"/usr/bin/vmware-toolbox" during an XFree86 session.

To use the vmxnet driver, restart networking using the following commands:
/etc/init.d/network stop
rmmod pcnet32
rmmod vmxnet
depmod -a
modprobe vmxnet
/etc/init.d/network start

Enjoy,

--the VMware team
[/I]

To launch VMware tools, am I supposed to remember to invoke the VMware Tools session each time by going to Terminal, and then typing: "/usr/bin/vmware-toolbox"?  Or is it supposed to install itself under "Applications" so I can access it more conveniently?

Thanks so much for everyone's help. You have been great, guys.

---

