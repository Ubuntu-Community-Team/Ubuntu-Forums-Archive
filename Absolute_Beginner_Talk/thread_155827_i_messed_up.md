---
title: "i messed up"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-04-05
ok i being impatient that i am i thought that i would download and install flight 6
of dapper , so i downloaded and burned an iso cd to install, the cd booted i whent through partitoning my 19gb hd on wich breezy is installed , i partitioned for flight 6
but when it began to install i kept getting a message that such and such file was corrupt , next file after next. now i have a 6gb partition with breezy and only 1.23 gb of free space, and a 12gb partition with nothing on it it is formated ext3. how do i merge my first with the second partition to give me13 bg of free space with breezy ?

---

### Post by Mustard on 2006-04-05
Using gparted or qtparted or whatever tool you have available from a live CD, you would delete the 12 gb partition to turn it into 'free space', then you would use the resize option to increase the size of the 6 gb breezy partition to take up the free space that you have just created. **You will have to do this from a live CD or something, as you can't resize a mounted partition, and your breezy partition will be mounted while you are running breezy.**  I notice you also have **two swap partitions** at the moment.  Only one is really required.  I would see which one breezy is currently using (consult your /etc/fstab file), and maybe keep that and then get rid of the second one.

While you are mucking around with partitioning, you might like to do some searching on the forum for how to move your /home folder to a separate partition.  It's a handy little trick that allows you to reinstall without formatting your /home partition, and by doing so you keep your user settings intact after a reinstall.

You could most likely just use the 12gb section you have now as your new /home.  Please read any instructions you find very carefully though, as you don't want to accidently lose all your /home settings.

This is how my system is setup at the moment...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
#/dev/hdb3       /media/puppylinux  ext2 user           0       0
#/dev/hdb1      /media/dsl      ext3    user            0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
mustard@slave:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         851     6835626   83  Linux
/dev/hda2             852        9729    71312535    5  Extended
/dev/hda5             852        1039     1510078+  82  Linux swap / Solaris
/dev/hda6            1040        9729    69802393+  83  Linux

```

---

### Post by abu-fatu on 2006-04-05
thank you mustard i did as you instructed got my partition up to its previous size. ? why would the iso dapper cd i downloaded have corrup files?

---

### Post by Mustard on 2006-04-06
[QUOTE=abu-fatu]thank you mustard i did as you instructed got my partition up to its previous size. ? why would the iso dapper cd i downloaded have corrup files?[/QUOTE]

Sometimes downloads can just become  corrupted, for reasons unknown (at least to me :D ).  Usually before burning the ISO to a CD, you would run an md5sum check on the ISO and compare it to the md5sums given at the download site.  If the 'hashes' are the same, that is the contain the same letters and numbers then that confirms that your download is ok.

The md5sum command is available in terminal. Try this command to read the manual for the md5sum command....

```
man md5sum
```

Type 'q' to exit the manual in terminal and return to a command prompt.

I believe that when downloading via a bittorrent link that md5sum checks are made as it is downloaded, so that file corruption is avoided during the download, so in the future you might like to try downloading an ISO from a torrent link, rather than a http or ftp link. I haven't tried any torrent links myself, but thats what I here anyway. :)

---

### Post by towsonu2003 on 2006-04-06
you might also want to burn iso to cd at a slower speed. I donno why, but I keep hearing it around here: so it should be correct ;)

---

### Post by Mustard on 2006-04-06
[QUOTE=towsonu2003]you might also want to burn iso to cd at a slower speed. I donno why, but I keep hearing it around here: so it should be correct ;)[/QUOTE]

Good point. I had forgotten to mention that one. :)

---

### Post by taurus on 2006-04-06
[QUOTE=towsonu2003]you might also want to burn iso to cd at a slower speed. I donno why, but I keep hearing it around here: so it should be correct ;)[/QUOTE]
Actually, I did a test with Dapper Flight 6 when it first came out.  I burnt it on a CD-RW (so I don't have to throw away CDs) at 12x and the thing wouldn't install.  It kept complaining about everything.  But then I burnt the same iso image, using k3b of course, at 4x, it installed just fine...  :)

---

