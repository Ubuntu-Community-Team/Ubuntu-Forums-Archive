---
title: "Thinking about compiling my own Kernel"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by carlosqueso on 2005-12-13
I've got the time and the processing power to compile my own kernel.  However, I heard that it has an effect on one's ability to recieve software updates via apt.  What will be the effects if I do compile my own?

---

### Post by matthew on 2005-12-13
[quote=carlosqueso]I've got the time and the processing power to compile my own kernel. However, I heard that it has an effect on one's ability to recieve software updates via apt. What will be the effects if I do compile my own?[/quote]The untimate answer is: it depends.

You won't be able to install security updates to your kernel via apt but would instead have to add them yourself, possibly recompiling your kernel. Not a super-huge deal, but if you haven't done it...

You will learn something and probably have some fun doing it.

If you have special modules (i.e. nVidia drivers, ipw2200, etc) you will have to reinstall them after you compile the new kernel. If you don't have these things this is not an issue. Again, it's not hard, but if you haven't done it before it takes some time as you learn how.

I would suggest you give it a go. Keep your current kernel(s) intact. If things don't work you haven't lost anything except a bit of your time and you will likely have some fun and learn something in the process.

---

### Post by carlosqueso on 2005-12-13
cool.....thanks

One more question...If i compile it specially for my processor, will I be able to use the packages in the normal i386 distribution of ubuntu? I have (I think) a k7 processor.

---

### Post by matthew on 2005-12-13
[quote=carlosqueso]cool.....thanks

One more question...If i compile it specially for my processor, will I be able to use the packages in the normal i386 distribution of ubuntu? I have (I think) a k7 processor.[/quote]Yeah. You will be able to use the other packages with no problems.

---

### Post by carlosqueso on 2005-12-13
Thanks...here goes.....

---

### Post by cstudent on 2005-12-13
I would be interested in hearing about your progress and what reference materials you used to help you learn how to do this.

---

### Post by carlosqueso on 2005-12-13
I'll let you know how it comes out.  I'm gonna compile my first kernel with: [http://doc.gwos.org/index.php/Kernel_Compilation](http://doc.gwos.org/index.php/Kernel_Compilation) that guide, and then move on to the one with the vanilla kernel in the same place.

---

### Post by matthew on 2005-12-13
[quote=cstudent]I would be interested in hearing about your progress and what reference materials you used to help you learn how to do this.[/quote]HI, cstudent,

I'm pretty sure you were asking carlosqueso, but I thought I would chime in with a few good basic links.

[https://wiki.ubuntu.com/KernelCompileHowto]("https://wiki.ubuntu.com/KernelCompileHowto")
[https://wiki.ubuntu.com/forum/software/CustomKernel]("https://wiki.ubuntu.com/forum/software/CustomKernel")
[http://ubuntuforums.org/showthread.php?t=85064]("http://ubuntuforums.org/showthread.php?t=85064")
[http://ubuntuforums.org/showthread.php?t=43065]("http://ubuntuforums.org/showthread.php?t=43065")
[http://ubuntuforums.org/showthread.php?t=65052]("http://ubuntuforums.org/showthread.php?t=65052")
[http://kernel.org/]("http://kernel.org/")

As to how I learned what little I know...trial and error. I have fought with my laptop (ATI graphics card which needs special drivers for 3D and an ipw2200 which wants it's own special drivers as well) but found compiling a kernel for my old AMD Duron testbox astoundingly easy. I'm no expert on this, but just by doing/failing/succeeding I've learned a little.

EDIT: I should include these two as well...glad you found the gwos one also!

[http://kernelnewbies.org/](http://kernelnewbies.org/)
[http://kernel.org/faq/](http://kernel.org/faq/)

---

### Post by cstudent on 2005-12-13
Thanks guys! I'll check out the articles. Although I don't know when I'm going to fit it all in. Right now I'm trying to brush up on my assembly programming for a microprocessor circuits class which starts after New Years, along with a C programming class. Plus the circuits class requires a Gentoo machine, which I have never worked with and have not even begun to put together. All this stuff to learn, I'm like a kid in a candy store. :D

---

### Post by carlosqueso on 2005-12-13
Well...my first attempt didn't work, it gave me an error about using intrd.....I guess my next step will be to look into one of matthew's howtos, and see what happens without using it.  Right now, I don't have time, so I'll get back to you after I try.

---

### Post by matthew on 2005-12-13
[quote=carlosqueso]Well...my first attempt didn't work, it gave me an error about using intrd.....I guess my next step will be to look into one of matthew's howtos, and see what happens without using it. Right now, I don't have time, so I'll get back to you after I try.[/quote]My first three attempts didn't work...typically because I tried to take out too many modules and ended up removing something I needed. :) Hang in there. Come back to it when you have some free time and you'll get it.

---

### Post by carlosqueso on 2005-12-14
Alright...I'm stuck...I compiled and got this when I tried to install the package ```
(Reading database ... 91530 files and directories currently installed.)
Preparing to replace kernel-image-2.6.12-t2 10.00.Custom (using kernel-image-2.6.12-t2_10.00.Custom_i386.deb) ...
Unpacking replacement kernel-image-2.6.12-t2 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-t2
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up kernel-image-2.6.12-t2 (10.00.Custom) ...
Cannot find /lib/modules/2(Reading database ... 91530 files and directories currently installed.)
Preparing to replace kernel-image-2.6.12-t2 10.00.Custom (using kernel-image-2.6.12-t2_10.00.Custom_i386.deb) ...
Unpacking replacement kernel-image-2.6.12-t2 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-t2
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up kernel-image-2.6.12-t2 (10.00.Custom) ...
Cannot find /lib/modules/2.6.12-t2
Failed to create initrd image.
dpkg: error processing kernel-image-2.6.12-t2 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kernel-image-2.6.12-t2
Failed to create initrd image.
dpkg: error processing kernel-image-2.6.12-t2 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kernel-image-2.6.12-t2

```  I tried compiling one without initrd, and got a kernel panic.  What can I do to get this to work?

---

### Post by carlosqueso on 2005-12-16
Thought I'd put up an update if you're still reading this, csstudent.  I stripped down my kernel (although I need to find out exactly what hardware I have, so I can strip it down further) and it compiled fine.  The problem with that whole mess up there was that I didn't have the initrd-tools package installed.  Once I installed that, the howto that I linked to works just fine.  It even somehow detected that I'm using xubuntu, and changed the splash screen accordingly.  If anyone who reads that knows how that happened, I'd be interested to know how.

---

### Post by cstudent on 2005-12-16
Yes I'm still reading this. I have subscribed to this thread. I'm glad to see you got things to work. I'm anxious to try my hand at doing my own kernel. I'm really interested in trying to roll my own Linux someday. I read an article a while back that started me thinking about a "pure" Linux distro. The latest stable kernel and  the actual "official" desktop of Gnome and compiling some apps from source like Firefox and Open Office, etc. Probably a nightmare waiting to happen, but I hope to start this project sometime after the new year.

---

### Post by carlosqueso on 2005-12-16
The roll your own idea sounds like a lot of fun....let me know how that comes out.  That's my project too for when I can get my hands on a testbed computer.  Of course, I'll be using Xfce instead of Gnome, but that's a personal choice.  Next time you get three or four hours (allowing for screwups and puzzling over your hardware), I'd definitely say just to jump in and compile a kernel.  If nothing else, you'll be able to claim supreme nerdiness over your friends (I know I did)

---

### Post by curtis on 2005-12-16
[http://linuxfromscratch.org](http://linuxfromscratch.org) :)

---

### Post by cstudent on 2005-12-16
Thanks for the link curtis.

---

