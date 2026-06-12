---
title: "Virtual Box Installation problem"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by erdley on 2007-11-17
Have proceeded to install Virtual Box on my Gutsy OS.  When I get to the point to attempt to start the new Virtual Machine I get the following error message:

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

How do I correct this problem?

Thanks for your help to a new Ubuntu user!

---

### Post by Dr Small on 2007-11-17
Greetings, and welcome to Ubuntu Forums.
Have you read this page ?
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Good luck!

Dr Small

---

### Post by daimaru on 2007-11-17
go to system-> admininstration->users and groups 
click on manage groups browse to vboxusers hit properties and check your username then hit ctrl+alt+backspace to restart xserver and log back in .. everything should work fine.

---

### Post by erdley on 2007-11-17
Thanks much for your helpful suggestion!  This corrects the problem that I initially reported, but now I get a message that the program cannot find bootable media.  My CD drive appears to be mounted and it contains a Windows XP Pro installation disk.  This disk is not directly bootable, apparently, but does contain a setup.exe file.  How do I create a bootable CD from this Windows XP disk?

---

### Post by daimaru on 2007-11-17
you could create an iso image of your cd first and then install windows from image in virtual box which is way faster by the way. so do this.
insert your windows cd (assuming your in ubuntu)
open terminal and type in this:
```
dd if=/dev/cdrom of=file.iso
```
after you copied the cd to file.iso or name it something else just select install form image in virtualbox and it might just work. 

hope that helps

EDIT: this is assuming that your not using some recovery disk as you sometimes get with laptops. it has to be a original winxp cd not one of the disks you get with a preinstalled system

---

### Post by erdley on 2007-11-17
Many thanks for your prompt reply!  Will give your helpful suggestion a go.

---

### Post by erdley on 2007-11-17
Thank you again!  Windows XP installed successfully by your suggested procedure.  My only significant problem is that I took all the default choices and now have the guest system operating with only about 2 Gigabytes of disk space, so I believe I will have to re-install, as I don't see any settings to change this partition size.  Windows seems to operate normally, and I could connect to the Internet, but this may not be a good idea considering the susceptibility of the Windows OS to virus and spyware attacks.

---

### Post by erdley on 2007-11-18
Have received a message that my USB ports are not installed.  The Windows XP guest system shows 488 MbBytes used by CD Drive with 0 bytes available, even though there is no CD in the drive.  It is possible to read the contents of any CD inserted into the drive, but nothing can be installed properly.  It may be that the 2 Gbytes allocated to this guest system is affecting this. Any help would be appreciated here, including how to reinstall the XP guest with USB ports enabled.

---

### Post by mistermax on 2007-12-01
I updated to 7.10 and get the kernel error. I've made sure that my vboxusers group has me in it and a check, but to no avail...

---

