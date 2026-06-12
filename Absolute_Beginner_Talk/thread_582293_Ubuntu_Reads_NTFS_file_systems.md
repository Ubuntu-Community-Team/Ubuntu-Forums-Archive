---
title: "Ubuntu Reads NTFS file systems"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by xsabrewulf on 2007-10-19
But why is the EXT3 drive not showing on my desktop. it only shows my NTFS file system harddrives.

Does linux not have a program files type folder where all installed programs go? where does the images and junk from firefox go?

---

### Post by jpeddicord on 2007-10-19
Regarding your second question:

Most programs install their core files into /usr/share and /usr/lib, with configuration in /var. With Firefox, your profile directory and cache is in /home/username/.mozilla/firefox.

Jacob

---

