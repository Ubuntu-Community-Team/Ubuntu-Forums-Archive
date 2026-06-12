---
title: "VirtualBox help"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Fonon on 2007-12-11
I'm trying to run the KDE4 version of Kubuntu on my copy of VirtualBox.  When I tried to start it(this is my frist VM), I get this message:


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
Obviously, Add/Remove didn't get those files, but I do need to know how to get it to work.  Some help, please?  Thanks.

---

### Post by Seisen on 2007-12-11
The package you need is called ```
virtualbox-ose-modules-2.6.22-14-generic
```

---

### Post by Fonon on 2007-12-11
virtualbox-ose-modules-2.6.22-14-generic is already the newest version.
virtualbox-ose-modules-2.6.22-14-generic set to manual installed.
The following packages were automatically installed and are no longer required:
  mplayer-skins libsvga1 libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

is the message I got.   the command i ran was
[CODE] sudo apt-get install virtualbox-ose-modules-2.6.22-14-generic[CODE]

I still get the same error message :(

---

### Post by skymera on 2007-12-11
why Virtualbox may i ask?

slow, GUI..

i prefer qemu, much quicker.

---

### Post by Fonon on 2007-12-11
I simply didn't know of any alternative.  I'll go check out Qemu, especially if it will solve my problem.

---

### Post by viciouslime on 2007-12-11
The problem is that instaling virtualbox doesn't actually do everything needed to setup virtual box. Firstly, you need to add yourself to the virtualbox group then you need to logout, back in then start the virtualbox kernel module, then it will work :)

These are one time only things, and if you want instead of logging out you can restart and then the kernel module will be started for you when the computer reboots. To add yourself to the group go to system/admin/users and groups :)

If you don't want to have to restart, the command to load the kernel modules is:```
sudo /etc/init.d/vboxdrv start
```

If you wonder where this comes from, check out the error message you posted :D

---

### Post by Fonon on 2007-12-11
Oops :p

Guess I should learn how to look at a criptic error message for more than a few minutes before requesting help.

Well, it works great now.  Thanks viciouslime!

@skymera: I tried out Qemu, but I couldn't figure out the GUI, and I'm usually good at that.  Perhaps it will work better in the future for me.

---

### Post by viciouslime on 2007-12-13
> **Fonon said:**
> Oops :p

Guess I should learn how to look at a criptic error message for more than a few minutes before requesting help.

Well, it works great now.  Thanks viciouslime!

@skymera: I tried out Qemu, but I couldn't figure out the GUI, and I'm usually good at that.  Perhaps it will work better in the future for me.

Nah, just learn that that's what that particular cryptic error message means. It's far safer to ask on here than just paste any old command it suggests into a terminal. If you've never loaded/unloaded a kernel module before you wouldn't know that that was the command.

Glad it's working for you now :)

---

