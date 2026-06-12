---
title: "editing xorg.conf without desktop"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by crabhunter on 2007-03-22
Hi,
I've screwed up my xorg.conf file.
I know what I've done but not how to fix it without a GUE.
I've tried the live cd but cannot find how to access the hard drive.
If I start in recovery mode how can I edit a file.
I have tried gedit /etc/X11/xorg.conf but it tells me to type gedit --help for details on command line options,but I can't find any.
I have tried ed /etc/X11/xorg.conf but all I get is a ?
I then tried apt-get ed and it told me I already have the latest version.
Using 6.10
Mike

---

### Post by Bachstelze on 2007-03-22
For a simple and intuitive CLI text editor, try *nano*.

---

### Post by anaconda on 2007-03-22
or more specifically:
nano /etc/X11/xorg.conf

but maybe you dont need to edit it.. there propably is an older backupversion in the same directory..

---

### Post by crabhunter on 2007-03-22
Nano worked a treat.
Thanks very much.
Mike

---

