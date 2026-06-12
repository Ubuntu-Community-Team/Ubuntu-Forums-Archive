---
title: "apache2 problem on FF desktop"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by soulsurf on 2007-05-15
I am having problems installing apache2 on Feisty Fawn 7.04  desktop edition. I execute
sudo apt-get install apache
all goes well until it asks for the Ubuntu 7.04 Feisty Fawn_ 7.04 Release i386 (20070415) cd. I pop the cd I installed from in my drive and it is found. Any Ideas?:confused:

---

### Post by chamberlain2006 on 2007-05-15
You need to install the apache2 package, first of all.  Also, you want to edit your /etc/apt/sources.list file to remove the cdrom entries, so that it will download the file from the internet.

---

### Post by annda on 2007-05-15
go to synaptic, disable the CD as repository to get the lates packages from internet, and
sudo apt-get install apache2

---

### Post by soulsurf on 2007-05-15
cheers, thats done the trick.

---

