---
title: "FTP with GUI?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Skylive on 2006-09-23
Hi! I understand that a similar question had been asked before, but unfortunatly, I have to ask about this again. I would like to have an FTP Server program with [COLOR="Red"]GUI[/COLOR] as I can't stand vsftp in the console... I couldn't get it to work at all. I'm a fan of Filezilla, but there seems to be a release everyday. I would like to have the program automatically updated using the updating program in Ubuntu. Any help available? If there is non available, would someone please tell me which is the correct version that I should download? Thank you in advance.

---

### Post by nts on 2006-09-23
> **Skylive said:**
> Hi! I understand that a similar question had been asked before, but unfortunatly, I have to ask about this again. I would like to have an FTP Server program with [COLOR="Red"]GUI[/COLOR] as I can't stand vsftp in the console... I couldn't get it to work at all. I'm a fan of Filezilla, but there seems to be a release everyday. I would like to have the program automatically updated using the updating program in Ubuntu. Any help available? If there is non available, would someone please tell me which is the correct version that I should download? Thank you in advance.

Why don't you install and configure vsftpd and have your clients utilize anonymous ftp - using Internet Explorer or FireFox ([ftp://serverip_or_hostname)?](ftp://serverip_or_hostname)?)

---

### Post by Skylive on 2006-09-24
My clients are not having a problem with anything...I'm the one that has problems. I used to host my files on a windows xp desktop computer using Filezilla. In Ubuntu, I need to be able to work with [COLOR="SandyBrown"]GUI[/COLOR] as I am simply horrible at using the console, in fact to tell you the truth, I'm still learning the very basics..

So I would like to know where I can get an GUI ftp server program, and at the same time, would someone like to tell me where I can go to learn how to use the console? Thank you in advance, esp. nts for replying.

---

### Post by wieman01 on 2006-09-24
Gnome ProFTP (gproftpd) it is. I am using it. Terrific & simple tool for configuration of ProFTP. See screenshot...
> sudo apt-get install proftpd
sudo apt-get install gproftpd

---

### Post by Skylive on 2006-09-24
Thank you sooo much. That is exactly what I wanted. A beautiful interface... this thread can now be closed.:D

---

