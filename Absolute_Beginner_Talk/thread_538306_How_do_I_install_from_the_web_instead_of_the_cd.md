---
title: "How do I install from the web instead of the cd?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by thetejon on 2007-08-29
I have a brand new install of 7.04 on a Thinkpad T61.  Everything is fine, except whenever I try to install something (apt-get or from the "add/remove" in the Applications menu), it asks for the install cd.  How do I tell it to get whatever files are needed from the web?

---

### Post by drs305 on 2007-08-29
Comment out the reference to the CD in the sources.lst file if you don't want to search the install CD for any future files.

---

### Post by bvmou on 2007-08-29
I think there was a typo, the file name is sources.list, located at /etc/apt/sources.list  -- you can edit out the cdrom by entering in the terminal 'sudo nano /etc/apt/sources.list' then placing # mark before the 'deb cdrom' lines.  Save and exit with control O then control X.

---

### Post by thetejon on 2007-08-30
Awesome.  Thanks very much for your help.

---

