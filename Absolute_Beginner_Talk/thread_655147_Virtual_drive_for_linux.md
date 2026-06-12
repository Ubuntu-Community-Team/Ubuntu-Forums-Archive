---
title: "Virtual drive for linux??"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by rock0nman on 2008-01-01
I have daemon tools for windows and want something that provides the same result for Linux.  I've tried to download and install CDEmu but to no avail.  It says and error wrong something to do with i386.  I'm running the AMD system.  NEED HELP! Thanks

---

### Post by PmDematagoda on 2008-01-01
You can try [AcetoneISO]("http://www.acetoneiso.netsons.org/viewpage.php?page_id=2"), it is a rather useful application.

---

### Post by shad0w_walker on 2008-01-01
What are you looking to do with the tool? There maybe another way around it with out needing CDemu. For example playing DVD movie backups directly from the ISO or just accessing files stored in the ISO.

Anyway, I believe your problem is you are running 64bit (I assume that is what your reference to the 'AMD system' points to.) and trying to install a 32bit version of cdemu. Where did you get cdemu from and have you looked for a 64bit version?

---

### Post by sonofusion82 on 2008-01-01
if you just need to open and ISO image, linux can easily do it without any additional tools using mount command like:

mount -t iso9660 -o loop isofilename mountpoint

---

### Post by hyper_ch on 2008-01-01
> **sonofusion82 said:**
> if you just need to open and ISO image, linux can easily do it without any additional tools using mount command like:

mount -t iso9660 -o loop isofilename mountpoint

Actually it's

```

sudo mount -t iso9660 -o loop /path/to/file.iso /path/to/mount

```

---

### Post by bulletxt on 2008-01-03
if you just need to mount an iso then do as they said, or else just install AcetoneISO2. it's very usefull and easy to use and does a lot of stuff ;)

---

### Post by WSmart on 2008-01-19
Does anyone know if any of these solutions provide emulation for gaming software?  I just loaded my first Linux this week, Ubuntu, and I love my Daemon Tools.  I never have to look for a CD.  And the CD's stay mounted between boots.  Programs load faster from the virtual drive.  And it's quiet.  I think virtual drives are the best thing that ever happened to optical drives-using it less and liking it more.  

Thanks!

---

