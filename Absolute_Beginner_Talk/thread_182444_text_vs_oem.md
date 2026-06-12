---
title: "text vs oem"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-05-26
Hi all, 

yesterday I decided to do a clean install of the dapper daily iso. Booted from the disk, and got several options, the top two being install in text mode, and install in oem mode - or something along those lines. 

tried to install in text mode, but it crashed when trying to install the base system, so had to abort. 

installed in oem mode, and it worked no problem. My question is though, what is the difference between the two? Will one allow me to do more? 

Thanks

Patrick

---

### Post by Sef on 2006-05-26
> what is the difference between the two?

To get the answer, click on > 

[OEM_Installer_Overview]("https://wiki.ubuntu.com/Ubuntu_OEM_Installer_Overview?highlight=%28OEM%29")

---

### Post by ozPATT on 2006-05-26
oh right, so the only difference is in the way the installation is carried out? thats cool. :) 

thanks for your help!

just a quick side question, am i also right in assuming that now I have installed the daily version, i just need to update each day and it will bring me up to speed with the next version?

---

### Post by Sef on 2006-05-26
You're welcome.  

> i just need to update each day and it will bring me up to speed with the next version?

1) It will let you know by an icon in the panel and a message that there are upgrades.

2) Open the terminal and type these commands:

sudo apt-get update

sudo apt-get upgrade

This will download any upgrades that have not been released yet, but are ready to go.

---

### Post by ozPATT on 2006-05-26
cool thanks :D

---

### Post by Sef on 2006-05-26
You're welcome.   Post whatever questions you have.   That way you will learn.

---

