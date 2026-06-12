---
title: "open source disk partitioning"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by RAV TUX on 2006-04-16
anybody have any experience with:
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
:confused:

---

### Post by teasum on 2006-04-16
I don't have direct experience with ntfsresize, but I have used Gparted several times (mentioned in the website you provided), and it's resized NTFS partitions for me with no problems.  I did defrag the partition before running the Gparted live CD, however, and regardless of what it says on thh website you provided in your post, I still think it's a good practice.  

As for open source partitioning tools, I highly recommend the Gparted Live CD.  The only drawback I've experienced is the inability to move NTFS partitions, although resizing them (i.e. from the end of the partition, not the beginning) has always worked fine for me.

---

### Post by RAV TUX on 2006-04-17
[QUOTE=teasum]I don't have direct experience with ntfsresize, but I have used Gparted several times (mentioned in the website you provided), and it's resized NTFS partitions for me with no problems.  I did defrag the partition before running the Gparted live CD, however, and regardless of what it says on thh website you provided in your post, I still think it's a good practice.  

As for open source partitioning tools, I highly recommend the Gparted Live CD.  The only drawback I've experienced is the inability to move NTFS partitions, although resizing them (i.e. from the end of the partition, not the beginning) has always worked fine for me.[/QUOTE]


Thanks Teasum...I  justed looked at Gparted and it looks great!...
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

also I just got off the phone with my new friend Tom...who suggested I use QT Parted:

[http://qtparted.sourceforge.net/faq.en.html](http://qtparted.sourceforge.net/faq.en.html)

:)

---

### Post by Sef on 2006-04-17
There's also ranish partition manager:

[http://www.ranish.com/part/]("http://www.ranish.com/part/")

---

### Post by teasum on 2006-04-17
I use the Gparted Live CD because it's quick and simple and, since it's a live CD, I just pop it in whenever I need to adjust my partition table before an install.  Does QT Parted have a live CD?  What about Ranish?  Just curious... it's always good to know what's out there and see what works best for you.

---

### Post by Sutekh on 2006-04-17
There is also [DiskDrake](http://qa.mandriva.com/twiki/bin/view/Main/DiskDrake)

[Ubuntu Forums - HowTo use DiskDrake for Partitioning](http://www.ubuntuforums.org/showthread.php?t=114142)

Only problems is that you have to download the whole PCLinuxOS ISO

---

### Post by steve.horsley on 2006-04-17
[QUOTE=yozef]anybody have any experience with:
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
:confused:[/QUOTE]
I have only used it once, so that's not an awful lot of experience. It worked perfectly, so that's a 100% success rate for me.

---

### Post by az on 2006-04-17
[QUOTE=yozef]anybody have any experience with:
[http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html](http://mlf.linux.rulez.org/mlf/ezaz/ntfsresize.html)
:confused:[/QUOTE]
The ubuntu installer can easily resize ntfs.  It uses that.

[http://packages.ubuntu.com/breezy/otherosfs/ntfsprogs](http://packages.ubuntu.com/breezy/otherosfs/ntfsprogs)

Very safe.  All parted frontends (as well as parted) use libr5aries like this for certain filesystems.  So if you use Gparted or Qtparted, you are using parted and ntfsresize.

---

### Post by teasum on 2006-04-17
Perhaps I'm too much of a noob, but I just prefer to set up the partitions graphically first, then proceed with the installation.  I've never had any problem with GParted, but, like I asked above, do these other partition tools come available as a live CD?

Also, and this is the big question for me, do any of these open source partitioning tools have the capability to *move* NTFS partitions?  I know GParted can only resize them (i.e. change the end point, not the beginning of the partition).

---

### Post by az on 2006-04-17
[QUOTE=teasum] do any of these open source partitioning tools have the capability to *move* NTFS partitions?  I know GParted can only resize them (i.e. change the end point, not the beginning of the partition).[/QUOTE]

Yes, provided you have enough disk space.  You cannot move the beginning of a partition.  You can copy it and then delete the original.  You just have to have enough space to be able to do step one before step two.

---

### Post by RAV TUX on 2006-04-17
for even more help (or confusion)....on disk partitioning refer to this thread:
[http://www.ubuntuforums.org/showthread.php?t=114142](http://www.ubuntuforums.org/showthread.php?t=114142)

:mrgreen:

---

### Post by az on 2006-04-18
[QUOTE=yozef]for even more help (or confusion)....on disk partitioning refer to this thread:
[http://www.ubuntuforums.org/showthread.php?t=114142](http://www.ubuntuforums.org/showthread.php?t=114142)

:mrgreen:[/QUOTE]
I seem to say "***" a lot in that thread..... Hmmmm.....

---

### Post by RAV TUX on 2006-04-19
[http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)

from a good friend of mine
;)

---

### Post by Sutekh on 2006-04-19
[QUOTE=yozef][http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)

from a good friend of mine
;)[/QUOTE]
I've been looking for that site all day!  I kept thinking is was herzan... not hezar...

Thankyou so much.

---

### Post by Charax on 2006-04-19
Gparted has a live CD? wow. my main problem with it was being unable to resize my root partition ('cos it was in use, obviously) I assume the Live CD would eliminate this problem?

Where can I find the .iso?

---

### Post by Sutekh on 2006-04-19
Its linked on the [GParted](http://gparted.sourceforge.net/) website

[GParted LiveCD](http://gparted.sourceforge.net/livecd.php)

Its around 30MB so go for it.

---

### Post by Charax on 2006-04-19
I love this forum, people are so helpful!

Hmm...anyone know how to put a boot loader onto a liveCD so I can burn an Ubuntu/GParted LiveCD? (Although it'd be kinda useless, as Ubuntu's liveCD has it's own partition manager).

---

### Post by Daniel McLaws on 2006-04-19
[QUOTE=teasum]Perhaps I'm too much of a noob, but I just prefer to set up the partitions graphically first, then proceed with the installation.  I've never had any problem with GParted, but, like I asked above, do these other partition tools come available as a live CD?

Also, and this is the big question for me, do any of these open source partitioning tools have the capability to *move* NTFS partitions?  I know GParted can only resize them (i.e. change the end point, not the beginning of the partition).[/QUOTE]

QTparted off of a Knoppix has the graphical display. Simplymepis also has a very simple one on their installation CD.

---

### Post by teasum on 2006-04-20
[QUOTE=Daniel McLaws]QTparted off of a Knoppix has the graphical display. Simplymepis also has a very simple one on their installation CD.[/QUOTE]

I might check those out next time I install/re-install Ubuntu.  That's the great thing about Open Source SW--you can choose what works best for you.

---

