---
title: "Turned off computer during update, anyway to recover?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by tombom on 2007-11-11
During the part of the update from 7.04 to 7.10 where it's installing packages - the bit where it says to not interrupt it - I was forced to turn off the computer as I'd misjudged the time it'd take. Now when I start it up and log in I get a blank grey screen with just a cursor. Is there any way to fix it without doing a full install?

---

### Post by elmosera on 2007-11-11
Sadly, no.
I would recommend booting to recovery mode and backing up your files from the text interface (if you can), and then doing a full reinstall.

---

### Post by mkoehler on 2007-11-11
Yes, there are, but it is time-intensive and I cannot guarantee that it will work.  When you get to the login screen, hit CTRL+ALT+F1 which will bring you to the TTY1 prompt.  If you log in as root, I've had success in running apt-get commands and package --reconfigure commands in order to repair the damage that has been done.  Good luck!

---

### Post by magicman5421 on 2007-11-11
if there isn't vital stuff on your drive, it is probably easier just to reinstall ubuntu from the 7.10 live cd.

---

