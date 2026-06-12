---
title: "Can play DVD movies but can't read discs?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by sfpeter on 2006-06-07
OKay, it seems I have the opposite problem everyone else haves with DVD's.  

I have an LG CD/DVD reader/writer combo.  It works just fine on playing DVD movies in Totem-Xine.  I can also read the contents of what is in the DVD movie directory.  Fine so far.

Night before last I noticed I couldn't read correctly dual layer discs I gad burnd on my Windows box.  Saw them, mounted, them, yet the discs were reading gibberish.  (one or two files, that's it.)  

This morning I burned a CD, but noticed I couldn't read any DVD's correctly, including movies.  I reinstalled my codecs and redid my fstab to:

# <file system> <mount point>   <type>  	<options>       	<dump>  <pass>
proc            /proc           proc    	defaults        	0       0
/dev/sda1       /               ext3    	defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    	sw              	0       0
/dev/hdc        /mnt/cdrom0   udf,iso9660	noauto,users,ro,dev	0       0
/dev/sdb	/mnt/optic1	vfat		noauto,rw,users		0       0
/dev/hdd	/mnt/optic2	vfat		noauto,rw,users		0       0

Now I can play movies again, but can't read CD's or DVD's.  Any ideas?

---

### Post by richbarna on 2006-06-07
Yeah, this is a weird problem that I had a little while back on Breezy.
[This Was My Post]("http://www.ubuntuforums.org/showthread.php?p=972218#post972218")
After I upgraded to Dapper and Re-installed Automatix everything suddenly worked again.
I would like to be able to give you exact details, but it just kind of sorted itself out.

---

### Post by sfpeter on 2006-06-07
Well, the CD readbility came back after a reboot, but DVD's are still gibberboo.   Can still play DVD movies all I want.  Guess I'll try redoing Automatix.

---

