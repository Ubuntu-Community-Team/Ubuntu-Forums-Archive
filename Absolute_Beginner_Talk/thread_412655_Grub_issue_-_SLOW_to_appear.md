---
title: "Grub issue - SLOW to appear"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by cliff0108 on 2007-04-18
I am running a dual boot system with Breezy Badger on one hard drive and Windows XP on the C drive.
When I installed Linux I installed Grub on the C drive to provide a menu for the dual boot.

Everything has worked perfectly for the past 2 years and I am easily able to boot to either system.

Lately however when I exit Linux and reboot - it seems to take forever for the grub menu to appear. I'm looking a t a black screen with a flashing cursor (anxiety  increasing :) ) Eventually it does come - but I am wondering if anyone has any idea why this is happening and what if anything to do.

I'm not sure what to do to get either operating system up if one of these days Grub does NOT appear.

I understand Grub is written to the MBR section of the C drive - and that's about all I know.

Thanks in advance for reading this.

Cliff

---

### Post by mac.ryan on 2007-04-18
I don't know what your problem is due to. Some hints might (or might not) be in your /boot/grub/menu.lst file (which says what menu entry to display, how, where, etc...). You can post it here, if you like.

On the MBR, really, there is only the instruction to run GRUB (it is called "stage 1") while the bulk of GRUB is on your ubuntu partition (/boot/grub).

As an extreme (yet safe) measure, If something went corrupted in your grub installation, you can simply reinstall it (follow [any]("http://ubuntuforums.org/showthread.php?t=224351") of the various how-to's around). Save your menu.lst file before... just in case!

You can also create an "emergency grub disk" that you can insert in case the installed version of grub one day dies. See "[the super grub disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")" project for more info.

A good general page to understand grub better is [here]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by cliff0108 on 2007-04-18
Thanks so much !
A great deal of information here which I will explore.
Gratefully,
Cliff

---

### Post by freebird54 on 2007-04-18
Just wondering here - is it that Grub is slow to appear - or that Linux is slow to shutdown?  Is Grub slow on a cold boot?  Is it slow when exiting Windows?  You get the idea I'm sure... :)

---

### Post by cliff0108 on 2007-04-19
I should have been more specific.
I tested it last night - if I do a cold boot - ie shut down rather than re-start, the Grub menu appears right away. If I restart then after all the exit/shutting down dialogue completes and the screen goes balck with a flashing cursor for approximately a minute before the Grub menu appears. 
I had thought Grub might be corrupted but given it works fine from a cold boot I gather not. It may just be that Ubuntu is taking longer to shut down - I'm not sure.
Thanks - Obliged for any further thoughts..
Cliff

---

### Post by freebird54 on 2007-04-19
I think you're right - it isn't a grub issue.  Does it happen from both (or all) OS's on shutdown?  Just Ubuntu?  Just Win?  

Isn't it fun trying to determine the actual source of problems?  We have become so used to frazzled software that we tend to forget that hardware sometimes has issues of its own.  In years past, the expectation was the other way around :)

---

