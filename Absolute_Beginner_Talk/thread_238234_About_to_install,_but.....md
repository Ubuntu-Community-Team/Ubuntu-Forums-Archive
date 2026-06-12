---
title: "About to install, but...."
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by jaybmx on 2006-08-17
I am way new to Ubuntu and I want to install it on one of my machines.  I installed on a laptop and i love it!

I have a machine that has 3 drives in it. One is the "system" drive and the other 2 are for media storage.  I use this machine to play music and surf the web and other basic stuff, so it will be a perfect place for me to practice/learn.

I am not worried about the "system" drive, i will let the Ubuntu installer format the drive and all that...
What will happen to the other 2 ntfs drives? Will I be able to mount and share them in Ubuntu no problem?
I guess I am a little paranoid about messin up my mp3s and videos!
Any advise on this install would be greatly appreciated!
Thanks!:KS

---

### Post by taurus on 2006-08-17
Just make sure you point the installer to whichever drive you plan to install it!  And before you click okay, double check.  Normally, the first drive is known as /dev/hda, second as /dev/hdb, and third as /dev/hdc...  Once you have Ubuntu on the first drive, you can mount the other two with no problem at all.  You can do that thru /etc/fstab.

---

### Post by PriceChild on 2006-08-17
Linux is unable to write to ntfs unless you go out of your way to install unreliable software designed to do so.

The installer should not touch your other drives but i really advise you to back up ALL important data that you couldn't live without. Don't say i didn't warn you ;)

Check out [http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php) & [http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html) for more help.

I also advise you to use the alternate installer cd if you have any grand partitioning plans. I always run into problems with the live cd's partitioner when trying to create complex partition tables.

Pricey

EDIT Don't forget to check every step literally half a dozen times to make sure you don't have to kick yourself later.

---

### Post by Greycloak on 2006-08-17
When I installed Ubuntu in a dual-boot configuration with windows there were no problems at all with my other drives/partitions.  As soon as I booted to Ubuntu hda1,hda5, and hdb1 (my ntfs partitions) showed up on the desktop.  As a matter of fact I use ryhtmbox to play all of my MP3s directly from hdb1.

---

### Post by jaybmx on 2006-08-17
Thats just what I wanted to hear Greycloak!

Thanks!

---

### Post by bodhi.zazen on 2006-08-17
Linux does just fine with NTFS. PriceChild's information is outdated.

I have a shared windows (work) USB Linux (home) drive. It is NTFS and I have no problem with read-write in either Windows or Linux.

You will have full access to your media, both read and write no problem from Ubuntu. You may need to modify /etc/fstab or permissions post install.

---

### Post by PriceChild on 2006-08-17
> **bodhi.zazen said:**
> Linux does just fine with NTFS. PriceChild's information is outdated.

Linux is fine in reading... However all free software out there which allows you to write to ntfs is labelled experimental and "use at your own risk" This is because microsoft hasn't released standards and the open source community is guessing.

Even if it is stable(ish) its still not perfect.

---

### Post by bodhi.zazen on 2006-08-17
PriceChild- Thanks for the info. I've been writing to (some) ntfs (data) partitions for 6 months without problems.

I DO NOT write to my windows partition.

Otherwise define "perfect". Data loss can occurr with any file system and the NTFS drivers have improved in the last few weeks.

---

### Post by givré on 2006-08-17
I would not call ntfs-3g experimental. If we follow the debian' way, it's more testing or unstable than experimental, but it's definitly not stable.
There is no magic driver for ntfs, there is just better one, and for the moment ntfs-3g is the better one. Have a look at the beginning of my HowTo to learn about the status of the different project [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

But we'll always have to labelize that : "use at your own risk"

---

