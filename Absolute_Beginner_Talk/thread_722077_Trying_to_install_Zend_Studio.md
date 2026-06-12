---
title: "Trying to install Zend Studio"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Jhorra on 2008-03-12
I did a search, but couldn't find anything recent on this.  I know I need java, but I don't know if that's installed or not.  I just installed Ubuntu 7.10 from the CD, but I'm not sure if Java came with it.  Once I get past that, I have a tar.gz file.  If I try to open that it opens a folder with a bin file in it.  I have no idea what to do from here.  Any help is appreciated.



Past that, I tried Ubuntu probably a year or so ago, and couldn't really get it to work with my computer.  They must have come a long way, because it installed with no problems on my Sony laptop, and everything appears to be working.  I can even write to my NTFS partition.  This is light years ahead of where it was the last time I tried it.

---

### Post by Nepherte on 2008-03-12
By default, the Java Runtime Environment is not installed. To install it:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
If you want version 5, just replace every 6 with a 5.

Afterwards jou navigate to the directory where the file is located and just untar the archive file:
```
tar xvfz filename.tar.gz
```
and I assume you'll have to execute the bin file, but I've never worked with Zend Studio, so I could be wrong.
```
sh binfile.bin
```
You might need sudo privileged for it to install (place sudo in front of the command).

---

