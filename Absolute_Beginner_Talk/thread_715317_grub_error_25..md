---
title: "grub error 25."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Tellahlieah on 2008-03-04
Ok, so today I was running the liveCD and after making up my mind I wanted to install it on a external hard drive, ok so I followed a guide on here
 (don't have the link since this is a different computer but was on here) but there was a guide on "How to install to an external hard drive" after partitioning my external from the guided 
partition and installing the OS it wanted to restart, well after the restart all I get is the infamous

loading grub
  grub error 25

even when trying to boot from the internal HD I receive this message as well and to my knowledge their is nothing I can do so any help 
would really be appreciated and I was looking forward to using :(

---

### Post by overdrank on 2008-03-04
> **Tellahlieah said:**
> Ok, so today I was running the liveCD and after making up my mind I wanted to install it on a external hard drive, ok so I followed a guide on here
 (don't have the link since this is a different computer but was on here) but there was a guide on "How to install to an external hard drive" after partitioning my external from the guided 
partition and installing the OS it wanted to restart, well after the restart all I get is the infamous

loading grub
  grub error 25

even when trying to boot from the internal HD I receive this message as well and to my knowledge their is nothing I can do so any help 
would really be appreciated and I was looking forward to using :(

Hi and welcome, there seems to be an issue with the grub and maybe this link will help.
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
Good luck!

---

### Post by jan quark on 2008-03-04
> 25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk.

also read through this related threads
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=53965](http://ubuntuforums.org/showthread.php?t=53965)
[*][http://ubuntuforums.org/showthread.php?t=439063](http://ubuntuforums.org/showthread.php?t=439063)
[/LIST]

right now I do not have a solution but will have a look at this thread and wait for inspiration

---

### Post by Tellahlieah on 2008-03-04
Ok playing in the BIOS I flipped on the install other OS option that only lets you boot with 258 RAM, it let me choose the OS Ubuntu , Ubuntu Rescue mode, XP
then seeing it work fine but only having 258 I restarted and turned 
this off and it seems to work fine now, but without the external HD plugged in I now get error 21
but can run windows and Ubuntu with all my ram being recognized, but I'd like to be able to boot without having to have the External HD plugged in and want it going straight to XP

---

