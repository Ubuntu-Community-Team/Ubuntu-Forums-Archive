---
title: "driver installation"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by tst76 on 2007-07-10
Have installed a USB dongle  for adapting to an ethernet connection.  I have a laptop with Ubuntu 6.10 installed and currently use a Belkin card for wireless connection.  When I upgraded to Feisty Fawn, however, I lost the internet connection, and eventually had to reinstall 6.10 to regain it.

The USB dongle has drivers for Linux available, and I downloaded the tar.gz file to my desktop. I seem to have compiled the necessary files, also to my desktop, but when I get to the command ./mosinst I get the following error list in my terminal :

mkdir: cannot create directory `/usr/lib/mos7830': File exists
cp: cannot create regular file `/usr/lib/mos7830/mcs7830.ko': Permission denied
insmod: error inserting 'mcs7830.ko': -1 Operation not permitted
grep: /etc/rc.d/rc.local: No such file or directory
sh: cannot create /etc/rc.d/rc.local: Directory nonexistent
chmod: cannot access `/etc/rc.d/rc.local': No such file or directory
grep: /etc/rc.d/rc.local: No such file or directory
sh: cannot create /etc/rc.d/rc.local: Directory nonexistent
chmod: cannot access `/etc/rc.d/rc.local': No such file or directory
steven@tst:~/Desktop/Linux_7830$ 
 

Have I compiled the file to the wrong place?  Does it have to be in a certain folder and the install command operated from there?

Thanks in advance

Steve:(

---

### Post by FleetAdmiral74 on 2007-07-10
well I see a permission denied thing, have you tried running it as sudo?

---

### Post by tst76 on 2007-07-10
Yes, tried that with the same results.

---

### Post by FleetAdmiral74 on 2007-07-10
You might actually need to run it as root. I know some poorly written programs don't play nicely with the temp admin privileges created by sudo...

---

### Post by tst76 on 2007-07-10
I'm not sure how to do that.  Will I have to move the files elswhere?

---

### Post by FleetAdmiral74 on 2007-07-10
The only way I know is to boot up into recovery mode...but that might not be too smart if you don't know what I am doing. And I rarely know what I am doing.

---

### Post by tst76 on 2007-07-10
I think that this is the problem.  It would seem that I don't have permission to write to the File System folder.

---

