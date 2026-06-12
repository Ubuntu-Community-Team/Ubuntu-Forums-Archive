---
title: "how I used a graphical image software to backup all parts of dapper drake as an image"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by vectoravtech on 2007-08-23
Ok I have a dual boot system so when I boot up I can choose to boot either xp or linux. What I used to image was Drive Image 2002 which when I started from the 2 bootable floppys I created it repaired 2 or 3 errors so I can make the image graphicly. After restoring a linux image I booted a Dapper Drake Ubuntu live cd with safe mode because I have a Sapphire X800 Video Card. [http://davidwinter.me.uk/articles/2006/10/25/getting-ubuntu-dapper-to-dance-with-ati-x800-gto/](http://davidwinter.me.uk/articles/2006/10/25/getting-ubuntu-dapper-to-dance-with-ati-x800-gto/)

At any rate To perform the Inode error fix I needed to do because I saw the error popup in Dapper Drake I booted the D.D. live cd and opened the terminal and sudo su then typed this:
1) umount /dev/sda7
2) fsck.ext2 -f /dev/sda7
3) fsck.ext3 /dev/ext2
4) mkdir /mnt/sda7; mount /dev/sda7/mnt/sda7

     After number two it should check and repair the Inode errors.
I'm not sure if anyone cares that I found this out but I decided to spread the word anyway. It works like a charm.\\:D/

---

### Post by vectoravtech on 2007-08-24
I give credit for the inode error fix to my buds on irc.

---

### Post by vectoravtech on 2007-08-27
I know its kind of dumb but im just letting people know that imaging can be done in graphical mode and you dont have to save it on an ftp server haha.:-s

---

### Post by SpiritIsReality on 2007-08-27
howdy

bookmarked

maybe you could add it to the tutorials and tips, and the wiki
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
[http://ubuntuforums.org/showthread.php?t=81999](http://ubuntuforums.org/showthread.php?t=81999)

trails

---

### Post by vectoravtech on 2007-08-27
After putting xp backup image back for ubuntu Dapper Drake and fixing the Inode error and remounting the linux partition I like to sfc /purgecache then sfc /scannow to repair the xp files. Its just a personal preference. Thankyou for your input; I will do it.

---

