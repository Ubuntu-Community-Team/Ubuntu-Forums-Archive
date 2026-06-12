---
title: "Lexmark printer"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by RHS on 2007-01-05
I have been experiencing Ubuntu 6.06 for about a week now, and am very satisfied.  I have a Lexmark Z515 printer.  The Lexmark website only offers drivers for Mac and Windows.  How do I use my printer?  Thanks so much!

---

### Post by Shatrat on 2007-01-05
There is this how-to on the subject.
[http://www.ubuntuforums.org/showthread.php?t=49714](http://www.ubuntuforums.org/showthread.php?t=49714)

The how-to is kind of old though, I would have thought a common printer like that would work out of the box by now.  My HP printer had no problem.

---

### Post by Vorian on 2007-01-05
You can install lexmark drivers thusly.....

step 1: get it ```
wget http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.deb
```step 2: install it```
sudo dpkg -i print-drivers-linux-glibc2-x86.deb
```then open root terminal and configure

step 3: configure it```
/usr/local/lexmark/setup.lexprint
```You will find it in apps/system tools...

---

### Post by louieb on 2007-01-05
Sad to say but[ linuxprinting.org]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z515") says your printer is good for a paperweight.
Lexmark printers are known for there incompatibility with Linux.
IMO HP printers are the way to go.

---

### Post by Vorian on 2007-01-06
It can be done.....
[URL="http://img120.imageshack.us/my.php?image=screenshottj1.png"]
[/URL]

---

### Post by petermck on 2007-01-06
Well done:D There seems to me plenty of Lexmark drivers in CUPS.

---

