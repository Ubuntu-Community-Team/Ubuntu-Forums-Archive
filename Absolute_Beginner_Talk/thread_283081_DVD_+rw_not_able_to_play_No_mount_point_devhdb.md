---
title: "DVD +rw not able to play? No mount point /dev/hdb"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-23
Hello, I'm trying to be able to play my DVD's +rw, and I am getting the same error saying that there is no mount point /dev/hdb?

I also had a different error last night when I tried to play my DVD's. The DVD/CD icon would appear on my desktop, and the files would show in the thunar, but then I would get an error and the files would freeze and I wouldn't be move up or down in the file system and I wouldn't be able to play the selected video file.

I have the codecs for DVD playback from the wiki page installed, am I missing something else?.

Thanks,
-c.

---

### Post by Jussi Kukkonen on 2006-10-23
> I am getting the same error saying that there is no mount point /dev/hdb?
Are you sure that is the exact error message? If so, I'd like to see your /etc/fstab file. Mount points definitely shouldn't point to /dev/*...

---

### Post by crimesaucer on 2006-10-23
I'm trying a few things right now with removing and installing new media players and libraries/codecs.

What code do I write into terminal for you to be able to see the fstab?

---

### Post by crimesaucer on 2006-10-23
Is this what you wanted to see?


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=67b4c5f2-50e6-490a-a0a7-ea7959414612 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=B444EE8344EE47A6 /media/hda1 ntfs nls=utf8,umask=0222 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=c99f14c1-6d47-45f4-934a-7c14085f187d none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Jussi Kukkonen on 2006-10-24
Yeah, that's it... and the cdrom line looks fine.

It's possible that the drive can't read that particular DVD-RW -- it happens... Does the drive read other DVDs or CDs ok?

what happens if your try
```
mount /media/cdrom0/
```
when you have a DVD in the tray?

---

### Post by crimesaucer on 2006-10-24
I did a -f install to fix any broken packages, I also installed VLC and all of the codecs and libraries it comes with, and re-installed all the codecs on the wiki as well as the DVD playback libraries. Then I also did a sudo apt-get update, sudo apt-get upgrade, and a sudo apt-get dist-upgrade and all of that fixed my problem except for one DVD with .avi files on it, and I haven't checked all of my DVD's and CD's yet, but most of the good ones that I've tested with movies I don't want to lose (Dune, Napoleon Dynamite, ect...) are playing perfectly. I also am liking XINE a lot more than any of the other media players so far. It seems to work best with xubuntu edgy.

Thanks anyway,
-c.

---

