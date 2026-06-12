---
title: "DVDplaying regioncode"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by derPhilipp on 2006-11-26
Correct me if I'm wrong with this:

When you use Xine and libdvdcss2 the complete decryption of the dvd is done by the software - normally parts of the css encryption are decrypted by the drive which will refuse to do his job when the regioncode is not matching.. Ergo: regioncode does not matter using softwaredecryption!
I'm playing region1 dvds on my region2 drive now for years with Xine.

derPhilipp

---

### Post by TheMono on 2006-11-26
This gets a little more complicated than that. There are two types of drives, RPC1 and RPC2 (at least, my memory says it is RPC, but that acronym may be wrong)

RPC1 has a soft region code, so the region is tracked by your OS, changes are tracked by your OS, etc. As far as I can tell, where windows has support for this, Ubuntu does not.

RPC2 is a hard region code that is written onto the drive itself, and will simply refuse to read the wrong region.

So, if you´ve been doing this for years, then you´re probably still using an RPC1 drive for years, which is completely believable.

---

### Post by derPhilipp on 2006-11-26
hey - you are right.. googled around and found this:

[http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/RegionFreeDVD](http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/RegionFreeDVD)

guess I'm lucky with my drive :)

---

