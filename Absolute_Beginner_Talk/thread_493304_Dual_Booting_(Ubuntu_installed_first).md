---
title: "Dual Booting (Ubuntu installed first)"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by creekbaum2 on 2007-07-05
I want to be able to dual boot XP and Ubuntu from the same hard drive. I have read in many places that it is best to install windows first, and then Ubuntu after. However, I have spent a great deal of time getting ubuntu to look and work how I want it to, so I would hate to have to reformat. Is there anyway to install XP after having Ubuntu installed? Or am I just out of luck?

---

### Post by annda on 2007-07-05
go ahead. you will have to reinstall grub from the live cd or super grub disk later. there are about 10000 pages about that. i recommend two:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by originald on 2007-07-05
Hi,

I'm only just starting to use linux myself but here are a few links to some information on how to achieve this

[http://en.allexperts.com/q/Unix-Linux-OS-1064/Installing-windows-linux.htm]("http://en.allexperts.com/q/Unix-Linux-OS-1064/Installing-windows-linux.htm")



[http://stepien.com.pl/2006/09/17/windows-after-linux/]("http://stepien.com.pl/2006/09/17/windows-after-linux/")

I did a [http://www.google.com]("http://www.google.com") with the search text installing windows after linux for these and there was plenty more there to read through.

Hope this helps

OriginalD

---

### Post by creekbaum2 on 2007-07-05
Thanks, exactly what I was looking for. Thanks for the quick responses.

---

### Post by rickycodie on 2007-07-05
after you install ubuntu just do what this link says it is much easier than most other things.

[http://ubuntuforums.org/showthread.php?t=456819](http://ubuntuforums.org/showthread.php?t=456819)

---

### Post by fallencyi on 2007-07-05
Hiya,

DISCLAIMER, I am pretty new to Ubuntu, but it is definately possible. I just did it.
Most people recommend installing windows first simply because it is much simpler.

Check out the following post. This has info for doing this  with multiple hard drives.:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)


The major difference for you would be that you need to make space on your existing Ubuntu Drive for windows:
1. Boot from a live CD & resize your Ubuntu  install to make some room for windows.
gksudo gparted, and
(All the normal caution about backups 1st apply)
Resize your partitions to make space for windows.

2. Install windows in the "unpartitioned space" you just created.
(NOTE: This will make you unable to get back to Ubuntu by default because Windows has a nasty habit of overwriting grub in the MBR )

3. Follow the thread above for fixing grub,  but with your disc/partition setup in mind.
(You need to understand that the numbers (hdx,x)  and (hdx) as outlined in the thread above apply to 
1st HDD = /dev/hda or /dev/sda  (in grub this is hd0)

You might also try google for "Supergrub Disk" for a utility that makes step 3, easier. Personally I had no luck with it, & ended up doing it manually, but several people here swear by it. 

Bottom line, is it's not as simple as a graphical installer, but it's do-able & there is plenty of experiance on this forum that can help you through it. Best of luck!!

---

