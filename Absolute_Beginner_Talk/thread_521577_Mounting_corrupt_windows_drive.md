---
title: "Mounting corrupt windows drive"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Skootles on 2007-08-09
Okay, so one of my Windows drives got corrupted somehow, and I was told to mount it in Ubuntu to be able to copy the files off of it (no problem, I've used Ubuntu before). However, when I try to mount it, it tells me to specify the filesystem. When I specify ntfs, I get this:

> mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any help? :(

---

### Post by oilchangeguy on 2007-08-09
try this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Skootles on 2007-08-09
Still have the same error..  ugh. Would it be easier to just format my drive, then use recovery software to retrieve what I could?

---

### Post by oilchangeguy on 2007-08-09
> **Skootles said:**
> Still have the same error..  ugh. Would it be easier to just format my drive, then use recovery software to retrieve what I could?

if you format the drive, there won't be anything to recover. in the future i'd suggest doing backup's of your data. there are companies out there that can recover your data. it's a question of how much do you want to spend, to get it back.

---

### Post by fumduck on 2007-08-09
have you tried a windows disk to see if you can do a file checker??

---

### Post by Rocket2DMn on 2007-08-09
If you can't force it to mount with the -f option in mount and you have ntfs-3g instaled, you're pretty much screwed.  You didn't show us your command, but I think you need to use "ntfs-3g", not just "ntfs", as the file system type.
We stress the importance of keeping good backups here, but most of us probably learned the hard way at some time or another.

---

### Post by brennydoogles on 2007-08-09
You could do a file recovery now if you wanted (before formatting). There is a program that can be installed via synaptic or terminal called Testdisk (Install using ```
sudo aptitude install testdisk
```) After you install it, you can run either it to try and repair the drive, or the included program Photorec to recover files (you would run it by typing ```
sudo photorec
``` into the terminal) Afterwards you could use a script that I wrote (which I will attach) to organize the files by filetype, and sort them out that way. For photos, I recommend using F-spot to organize them by year, month, and day, and then a batch rename script (which I will include) to rename them from there. Can you tell I have done this a few times?? Hope this helps!!

---

### Post by louieb on 2007-08-09
I've had real good luck with the [URL="http://www.sysresccd.org/Main_Page"]SystemRescueCd
[/URL]. It has the two programs that ***brennydoogles*** sugested.

---

