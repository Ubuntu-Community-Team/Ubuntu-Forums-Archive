---
title: "[SOLVED] I need to remove Ubuntu and GRUB..."
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by nachomania on 2008-01-03
During the past week, I switched to Ubuntu from Debian. A ton of things worked better. But my graphics card didn't. It's a troublesome Nvidia. Either way, I used Envy to install a restricted graphics driver. It resulted in a super-messed up desktop, which remained after I uninstalled the driver. I now want to just get rid of Ubuntu (not as agressive as it reads, I'm quite calm), but GRUB is stopping me. I can't use any LiveCD at all. I only have the option of booting into my broken Ubuntu. How can I get rid of/fix GRUB? If I get rid of it, will I still be able to install an OS off a LiveCD? :confused:

---

### Post by NullHead on 2008-01-03
Use super-grub to remove grub and then when you're able to boot into  a live cd then use it's partitioning program to do the rest. 

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by nachomania on 2008-01-03
I can't boot any cds though

---

### Post by unclejac on 2008-01-03
Does your machine not check for bootable media before the Grub loader starts? Check in your machines BIOS, for the boot order. 

1 = CD/ DVD 
2 = HDD1
etc . . .

---

### Post by nachomania on 2008-01-03
Oh...:oops: 
Well, I've now booted a PCLOS Cd. Bye for now... :-({|=

---

### Post by NullHead on 2008-01-03
I've got a boot menu that I press f11 for. You might try that and also try out what unclejac suggested.

---

