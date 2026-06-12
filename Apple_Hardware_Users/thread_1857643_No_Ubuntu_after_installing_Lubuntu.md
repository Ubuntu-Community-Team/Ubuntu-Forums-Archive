---
title: "No Ubuntu after installing Lubuntu"
date: 2011-10-10
forum: Apple Hardware Users
---

### Post by canhoto on 2011-10-10
Hi.

I installed lubuntu, to try it, and I wanted to change from ubuntu to lubuntu. I googled it and I ran the folowing command:```
sudo dpkg-reconfigure gdm
```and I choosed the othe lxdm or something like that.

I restarted and... nothing happens. Nor lubuntu nor my good ubuntu.

"Nothing happens" means the screen (after the yaboot screen) gets black and, after a while, my monitor says "no signal" and goes to sleep.

I tried the Ctrl+Alt+F1(a little after the yaboot screen) but nothing happens.

So I need urgent help to get back to my Gnome Ubuntu desktop and to know kow to change desktop environments easily.

---

### Post by garvinrick4 on 2011-10-10
Put in your Live Cd (install CD using Try Ubuntu) and run this and post:
```
sudo fdisk -l
``` Lower case L

---

### Post by garvinrick4 on 2011-10-10
> So I need urgent help to get back to my Gnome Ubuntu desktop and to know kow to change desktop environments easily.
You have to reboot from one install to another, they should be on separate partitions or should be if you did not over write Ubuntu when installed Lubuntu. Run code in previous
post so we can see a bit of what is there.

---

### Post by canhoto on 2011-10-10
> **garvinrick4 said:**
> Put in your Live Cd (install CD using Try Ubuntu) and run this and post:
```
sudo fdisk -l
``` Lower case L 

I ran it and the result is

> ubuntu@ubuntu:~$ sudo fdisk -l
/dev/hda
        #                    type name                  length   base      ( size )  system
/dev/hda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled                2048 @ 64        (  1.0M)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled              204800 @ 2112      (100.0M)  Linux native
/dev/hda4         Apple_UNIX_SVR2 untitled            72878907 @ 206912    ( 34.8G)  Linux native
/dev/hda5         Apple_UNIX_SVR2 swap                 4080510 @ 308501298 (  1.9G)  Linux swap
/dev/hda6         Apple_Bootstrap untitled                1954 @ 73085819  (977.0k)  NewWorld bootblock
/dev/hda7         Apple_UNIX_SVR2 untitled           225759766 @ 73087773  (107.7G)  Linux native
/dev/hda8         Apple_UNIX_SVR2 swap                 9653759 @ 298847539 (  4.6G)  Linux swap

Block size=512, Number of Blocks=312581808
DeviceType=0x0, DeviceId=0x0

/dev/hdc
        #                    type name                length   base    ( size )  system
/dev/hdc1     Apple_partition_map Apple                    2 @ 1       (  1.0k)  Partition map
/dev/hdc2               Apple_HFS Ubuntu 8.04.1 ppc  1392104 @ 16      (679.7M)  HFS

Block size=512, Number of Blocks=1392120
DeviceType=0x1, DeviceId=0x1

I must say that I have Yellow Dog installed on the same HD *although I do not intend to use it since Ubuntu is - was! - running okay)

---

### Post by rsavage on 2011-10-10
Boot into single user mode.  Do this by typing "Linux single" at the second yaboot prompt.  Then run your reconfigure command again and select gdm as the default.  Reboot with "sudo reboot".

---

### Post by canhoto on 2011-10-10
> **rsavage said:**
> Boot into single user mode.  Do this by typing "Linux single" at the second yaboot prompt.  Then run your reconfigure command again and select gdm as the default.  Reboot with "sudo reboot".

Thanks! It worked. I don't know what happened with the Lubuntu desktop. Maybe I will just remove it.

---

### Post by rsavage on 2011-10-11
You've got two login managers installed so maybe they were clashing?
 
The thing about lubuntu is that it is all about lightness so I'm not sure you'll have the full effect installing it on top of normal ubuntu.  You should be able to select lubuntu as a session from the gdm login manager to try it.

---

