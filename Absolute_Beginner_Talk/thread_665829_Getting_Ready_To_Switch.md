---
title: "Getting Ready To Switch"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-12
Hello to All,

Here's hoping someone can help me.  I am pretty much ready to install ubuntu, but I'm new at this stuff.  So I need some help.

I had planned on following this walkthrough on how to set-up a dual boot system [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) but when it came time to partioning my drive windows is not allowing me to.  Shrink volume says that 0 MB are available to shrink on my hard drive.  

System Data:
HP MediaCentre PC
1 Hard Drive already partitioned (C drive and D drive for recovery to factory settings XP)
C drive currently has 215 GB free (docs are all off for safety/backup)
C drive is using Page File
Running Vista (I KNOW)
Ubuntu 7.1 LiveCD

I guess I'm looking to find out if it's SAFE to disable virtual memory to partition the drive, or if there are any other suggestions?  Do I need a 3rd party s/w to split things up?
Is the Virtual D drive the problem?  I would like to keep that, it's kind of the Penultimate safety blanket if all else fails.

I hope that even though I'm new, that I was able to at least make sense enough that you can help a fella out.

Cheers!

---

### Post by eolson on 2008-01-12
Hmmmm.   From the info you posted,  you have XP installed and the link is for Vista.  Is this correct?


Ooooops stupid me.  I didn't read the whole post.


Are you trying to install from the live CD?

---

### Post by durdensbuddy on 2008-01-12
Yes I am currently running Vista, and no haven't gotten to the point of installing yet.  I thought partitioning first would be necessary

---

### Post by Caduceus on 2008-01-12
Chances are this won't solve your problem, but when I first dual booted (not two days ago :D ) I had to use my Vista recovery disc to install Windows onto the whole drive, then shrink it.

It sounds like an obvious question, but is your drive too full to partition?

---

### Post by eolson on 2008-01-12
Yes, partioning is part of the process.

I've done quite a few with XP,  but never Vista.  XP from the live CD is easy,  basically just take all the defaults.   Whether Vista is the same,  don't know.    I'll research it and see what I can find.  Meanwhile somebody else may be along who has first hand experience.

Hang in there.

Ed

---

### Post by geirha on 2008-01-12
The insaller on the ubuntu CD can resize the windows partition, and create all the necessary partitions it needs. Though, defragment the windows partitions in windows first.

The installer should also detect windows, and set up dual booting for you. On some system it doesn't quite manage this though, so it's a good idea to burn out the Super Grub Disk first, which should fix you up if things don't go quite as planned.

---

### Post by durdensbuddy on 2008-01-12
It shouldn't be.  I cleaned it up of all documents so i have 215 GB free of 289 Gb.

Thanks for all the advice, currently defragging as we type.  :)  Really excited to get my geek on!  and escape windows

---

### Post by wolfen69 on 2008-01-12
defrag windows, then put in live cd, open terminal, type in sudo su, then type in gparted. you will have to unmount the windows drive first with (in terminal) umount /dev/whatever your drive letters are.

you should be able to resize your windows partition.

---

### Post by eolson on 2008-01-12
I'm back from my research project and the previous posters have pretty much summed it up.

---

