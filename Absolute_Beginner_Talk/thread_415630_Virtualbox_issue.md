---
title: "Virtualbox issue"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Mr.Kuchinawa on 2007-04-20
I'm running XP in virtualbox, but after I upgraded to feisty, I get this error message after trying to boot it:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

----

When I type what I'm told to, It looks like I'm supposed to type something, but I have no idea what. So what to do?

---

### Post by kyphi on 2007-04-20
You need to install VirtualBox on Feisty.

If you have a driver issue after that, use

# chmod 666 /dev/vboxdrv

If you have a permission issue, use

#usermod -G vboxusers -a <your userid>

---

### Post by steve.horsley on 2007-04-20
The virtualbox installer compiles against the kernel sources so the driver it installs is very kernel specific. After upgrading the kernel. you will need to reinstall VB to get the driver updated. That involves installing the build-essentials package and linux headers of course.

---

### Post by MRiGnS on 2007-04-20
you don't need to reinstall it.

run /etc/init.d/vboxdrv setup

you will need the build-essential and your kernel source though.

---

### Post by Mr.Kuchinawa on 2007-04-21
I'm kinda like a n00b. Care to write excately what I am supposed to type? It would be most appreciated.

---

### Post by MRiGnS on 2007-04-21
> **Mr.Kuchinawa said:**
> I'm kinda like a n00b. Care to write excately what I am supposed to type? It would be most appreciated.

```
sudo apt-get install build-essential linux-source
```
```
sudo su
/etc/init.d/vboxdrv setup
exit
```
```
sudo chmod 666 /dev/vboxdrv
sudo usermod -G vboxusers -a <your userid>
```

---

### Post by frankeleone on 2007-04-22
Hi,
         I have been following this thread to solve my virtualbox problem that I have been having since upgrading to Feisty, but I can't get it going. After upgrading to Feisty, Virtualbox wouldn't run because it said it could not find the kernel module. I uninstalled the program and reinstalled it. It says that the compilation of the kernal module failed. When looking at the install log to see why the kernel module does not compile, it says:
Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.
I have since run sudo apt-get install build-essential linux-source , which seemed to go fine
I have also tried sudo chmod 666 /dev/vboxdrv, which then says:
chmod: cannot access `/dev/vboxdrv': No such file or directory

As I am noodling around, I discover that vboxdrv.ko is in /lib/modules/2.6.17-10-386/misc

I am a nooby. I am not sure what all of this means, but...I can't get Virtualbox to work anymore since upgrading to Feisty and would appreciate any help. If you could spell it out on the command line, that would also help. Thanks, Frank

---

### Post by MRiGnS on 2007-04-22
try:

```
sudo apt-get install linux-headers-`uname -r`
sudo su
/etc/init.d/vboxdrv setup KERN_DIR=/usr/src/linux-headers-`uname -r`
exit
```

`uname -r` will grab the kernel name you are using at the moment.

if you already got the headers just skip the apt-get point and follow the other steps. this "should" solve your problem.

oh, and don't forget sudo chmod 666 /dev/vboxdrv afterwards.

---

### Post by frankeleone on 2007-04-22
Thank you for your quick respose. Unfortunately...

I ran both commands just in case. After running the second one, I got:

frankeleone@linuxbox:~$ sudo /etc/init.d/vboxdrv setup KERN_DIR=/usr/src/linux-headers-`uname -r`
Password:
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ]
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ]
 * Starting VirtualBox kernel module vboxdrv
 * No suitable module for running kernel found.


Any other ideas? Thanks for your help, Frank

---

### Post by MRiGnS on 2007-04-22
please read my post carefully. dont use sudo for this. use sudo su. and then perform the task.

---

### Post by frankeleone on 2007-04-22
You did it! Thank you so much! Frank

---

### Post by MRiGnS on 2007-04-22
> **frankeleone said:**
> You did it! Thank you so much! Frank

you're welcome pal

---

