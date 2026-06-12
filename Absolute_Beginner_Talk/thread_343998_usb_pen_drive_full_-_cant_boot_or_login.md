---
title: "usb pen drive full - cant boot or login"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by pcooklin on 2007-01-22
Hello - Im new to ubuntu. I bought a usb pen drive with ubuntu on it which has been working fine. My problem is that I tried to install kde on the pen drive which has completely filled the drive up to the point that it now cant boot. I get an error saying its too full to save the password. 

On the pend drive s has some tools like: gparted and terminal but the terminal only takes me to: root@gparted and not the main system Im trying to boot from. I realise I need to try and uninstall kde but dont know how to access the drive to do so. I have a live cd to work from but again, when I try to delete some files manually from the pen drive using the live cd it says I dont have permission to do so...Im stuck..if anyone can offer some help I would be grateful.

I dont want to install ubuntu to my main hard drive as I enjoy the mobile option of the pen drive...

Many thanks in advance.
Paul.

---

### Post by scrooge_74 on 2007-01-22
boot up with the Live CD

open a terminal, mount the drive

then sudo rm -rf what ever files you dont want

if the /home/users are in the drive go to the users folders and 

sudo rm -rf .Trash/*

so you can make space

you can do that also for the root account

---

