---
title: "Installing on an &quot;Autistic&quot; Laptop"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by James_Nostack on 2006-09-01
I was using Ubuntu 5.10, but my hardware crashed repeatedly during the upgrade to 6.06, and now the laptop is severely messed up.  I would like to upgrade (or install) 6.06, if possible.

Ultimate Question: how do I get the machine to boot off 6.06 CD?  (Or, how do I restore my 5.10 system and complete the install?)

Details:

When I boot from the HD, Grub 1.5 comes up, it uncompresses Linux, and then I get thousands of "segmentation faults".  (I don't know what that is.)  Then I get an error message: "ALERT!  /dev/hda1 does not exist.  Dropping to a shell!"  (If I understand this right, it's saying the HD doesn't exist.)  I get a shell prompt, but I'm too stupid to know what to do about it.

When I try to boot from the Live CD (and the Alternate CD), the drive lights up, but doesn't seem to be reading.  The computer eventually gives up, and tries to boot from the HD, giving the same error.

Essentially, my computer no longer boots from outside sources, and whatever's inside isn't working right.

Specifications: Toshiba Satellite 5005-S504, formerly running Ubuntu 5.10.

---

### Post by TFX360 on 2006-09-01
> **James_Nostack said:**
> I was using Ubuntu 5.10, but my hardware crashed repeatedly during the upgrade to 6.06, and now the laptop is severely messed up.  I would like to upgrade (or install) 6.06, if possible.

Ultimate Question: how do I get the machine to boot off 6.06 CD?  (Or, how do I restore my 5.10 system and complete the install?)

Details:

When I boot from the HD, Grub 1.5 comes up, it uncompresses Linux, and then I get thousands of "segmentation faults".  (I don't know what that is.)  Then I get an error message: "ALERT!  /dev/hda1 does not exist.  Dropping to a shell!"  (If I understand this right, it's saying the HD doesn't exist.)  I get a shell prompt, but I'm too stupid to know what to do about it.

When I try to boot from the Live CD (and the Alternate CD), the drive lights up, but doesn't seem to be reading.  The computer eventually gives up, and tries to boot from the HD, giving the same error.

Essentially, my computer no longer boots from outside sources, and whatever's inside isn't working right.

Specifications: Toshiba Satellite 5005-S504, formerly running Ubuntu 5.10.



Can you when you entered the shell do


```
sudo shutdown -rFf now
```

This wil force a check of your harddisk

pay attention and write down the disk he is scanning and lets hope its not /dev/hda1

---

### Post by James_Nostack on 2006-09-01
Actually, it turns out that "sudo" and "shutdown" are not found.  Here's what the screen looks like now...

```
Segmentation fault
Segmentation fault
[repeated many times]
Segmentation fault
ALERT!  /dev/hda1 does not exist.  Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job controll turned off
#

```
(It always does that.)  So I typed...

```
# sudo shutdown -rFf now
/bin/sh: sudo: not found
# shutdown -rFf now
/bin/sh: shut down: not found
# 
```

...which is perhaps not expected?  (I'm not sure what's happened.)

---

### Post by etherstream on 2006-09-01
Hmm, yeah it sounds like you have a sticky situation.

I'm not sure how it applies in this case but a segmentation fault is when a program tries to access a memory location that it isn't supposed to.  The linux kernel is normally supposed to take care of memory management, but it sounds like when you installed Ubuntu 6.06 the kernel was not installed correctly.  This may have been from errors reading the cd (scratched cd perhaps?).  

My guess would be that you're out of luck in trying to get your current installation running again and that you should just try reinstalling Ubuntu 6.06 with a different install CD.

---

### Post by James_Nostack on 2006-09-01
Thank you for that explanation.  The upgrade from 5.10 to 6.06 was done through Upgrade Manager, but there were multiple hardware crashes along the way, and it's probably mucked up the kernel.

> My guess would be that . . . you should just try reinstalling Ubuntu 6.06 with a different install CD

Unfortunately, the CD-ROM drive doesn't recognize _any_ CD--I tried 6.06 CD, Alternate 6.06, the 5.04 Live CD; all of these work fine on my Windows laptop.

So whatever problem I've got, it lets the CD-ROM drive spin and make a few noises, but it doesn't recognize what it sees. 

But that makes me wonder: if the HD doesn't work, and the CD-ROM doesn't work, how do I give boot instructions?

---

### Post by James_Nostack on 2006-09-01
Confirming the previous post: I just tried booting from an old Windows CD, which gives...

```
This drive is not supported.
Ending process.
Turn off the computer.
A:\>
```

---

### Post by TFX360 on 2006-09-02
> **James_Nostack said:**
> Confirming the previous post: I just tried booting from an old Windows CD, which gives...

```
This drive is not supported.
Ending process.
Turn off the computer.
A:\>
```

Could you check the insides of your computer? Just to be sure!

---

### Post by James_Nostack on 2006-09-02
I don't mind, but what should I look for?

---

### Post by James_Nostack on 2006-09-02
I have not opened my computer yet.  But I did press Esc when Grub 1.5 first appeared on the screen, which lets me choose from several kernels.

The default choice, "Ubuntu, kernel 2.6.12-10-386" gives me thousands of Segmentation Faults, and says ALERT! /dev/hda1 does not exist.  Dropping to a shell!

kernel 2.6.12-10-386 (recovery mode) = same problems

kernel 2.6.12-9-386.... seems to work!  And puts me into my desktop.  /me = so happy!!!!!!!!!  (I'm still not sure my CD drive is working, but that might require a different thread.)

So - what's the difference between kernel 2.6.12-10-386 and 2.6.12-9?  Is 12-10 my botched 6.06 install?

---

### Post by TFX360 on 2006-09-02
Is that a stable kernel? I didn't think so. Someone correct me if I'm wrong.

I'm running:

```
root@tfx-laptop:/home/tfx# uname -r
2.6.15-26-386
```

Witch is unstable too.


If you didn't make, install, compiled anything you could update your kernel to the latest build.


```
sudo aptitude update; sudo aptitude upgrade; sudo aptitude dist-upgrade
```

---

