---
title: "hardcore newb trying to figure things out"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by SigmaX6 on 2006-12-17
hey all I actually have just got ubuntu installed took me two days as Im rather newb to a linux enviroment. used windows since as far back as i can remember. Im happy with the install after reading for two days straight install went fine. I have a couple questions about ubuntu that i hope someone could answer.

these could be rather newbish.

1.im having a issue getting wine to run anything as i cant seem to get my head around it. i understand you bring up the terminal and type wine (whatever) to get stuff running. but ive been surfing around for some time trying to figure out why i dont have any drive letters. i have a file system(which i dont have access to create files/folders in) but no drive letters. I did install ubuntu from the live bootup and formatted my hdd ext3. So why do i have no drives setup/showing?

ex: under places i have two cdroms, Computer but no drive letters???

2. is there anyway to get ubuntu to recognize my various ntfs drives. Only drive that i have been able to get to showup in places is a usb drive. But it will not let me copy to it only read status

---

### Post by d3v1ant_0n3 on 2006-12-17
For mounting your windows partitions, check out this link:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by reiatzu on 2006-12-17
'1.im having a issue getting wine to run anything as i cant seem to get my head around it. i understand you bring up the terminal and type wine (whatever) to get stuff running. but ive been surfing around for some time trying to figure out why i dont have any drive letters. i have a file system(which i dont have access to create files/folders in) but no drive letters. I did install ubuntu from the live bootup and formatted my hdd ext3. So why do i have no drives setup/showing?'

In order for wine to work, you need to download and install the package:

First, add repository for Wine:
Type this in your terminal:
 
gksudo gedit /etc/apt/sources.list

 Add the following lines at the end of this file 

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

Save the edited file then type in:

sudo apt-get update

Wait for your sources to update, then type in

sudo apt-get install wine


After this is complete, type in: 

wine WhateverApplication


2. is there anyway to get ubuntu to recognize my various ntfs drives. Only drive that i have been able to get to showup in places is a usb drive. But it will not let me copy to it only read status

Ubuntu when dual booted should recognized and mounted your NTFS partitions, if it doesn't enter:

cd /media


This is the default directory for 'Media' ;) If it is mounted it should be on there, else it isn't mounted, or it doesn't exist.

---

### Post by Littleweseth on 2006-12-17
> **SigmaX6 said:**
> but ive been surfing around for some time trying to figure out why i dont have any drive letters. i have a file system(which i dont have access to create files/folders in) but no drive letters. I did install ubuntu from the live bootup and formatted my hdd ext3. So why do i have no drives setup/showing?

ex: under places i have two cdroms, Computer but no drive letters???

2. is there anyway to get ubuntu to recognize my various ntfs drives. Only drive that i have been able to get to showup in places is a usb drive. But it will not let me copy to it only read status

The Linux filesystem is rather different to the Windows way of doing things.
a) Permissions are very strict. You can mess around and do anything you want in your own home directory, /home/your-username, but messing around in the root directory ( '/' ) is a privilege reserved for the superuser. This is a Good Thing - it makes for a more secure computer, since mere-mortal users don't have the power to, for example, replace the Openoffice.org executable with something more malicious, or edit the startup scripts to wipe all harddrives on boot.

b) There are no 'drive letters'. Linux uses a slightly more flexible model to access storage media (hard drives, optical drives, usb sticks, et. al.) whereby they are 'mounted' under the root filesystem in a directory called '/mnt' or '/media'. For example, C: might translate to /mnt/hda1 and D: might translate to /mnt/hda2.

Check /mnt and /media to see if your NTFS drives are listed there.

Further reading on the linux filesystem : [http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by ickyfeet on 2006-12-17
As far as wine is concerned you can open a terminal and run:

sudo winecfg

it will open a window and you will want to click the "Drives" tab then click "autodetect"

it should populate the various cd-roms you have mounted and assign drive letters to them.  you might want to click the "Show advanced" button, highlight the drive letters and make sure your cd-roms show up as "cd-rom" under type  click OK and you're ready to go.

---

### Post by bodhi.zazen on 2006-12-17
[QUOTE=ickyfeet;1900451]As far as wine is concerned you can open a terminal and run:

sudo winecfg

it will open a window and you will want to click the "Drives" tab then click "autodetect"/QUOTE]

That sometimes works.

You should run winecfg as a user, not as root :)

Just:```
winecfg
```Without the sudo :p

---

### Post by SigmaX6 on 2006-12-17
hey this is sorta related aswell but i used wine to install a game into H as its the only drive letter that it let me into, but i need to access that dir manually through gui to copy files into it? how would i do this?](*,)

---

### Post by macogw on 2006-12-17
cd ~/.wine/drive_c

---

### Post by 3rdalbum on 2006-12-18
> **SigmaX6 said:**
> hey this is sorta related aswell but i used wine to install a game into H as its the only drive letter that it let me into, but i need to access that dir manually through gui to copy files into it? how would i do this?](*,)

Drive H in Wine?

Open a file browser window in your home directory, and press Control-L. At the end of the location bar, type:

```
/.wine/drive_h
```

Press Return. (the whole bar should be something like this: /home/username/.wine/drive_h)

If that doesn't work, get rid of the "drive_h" bit, press Return, and you'll be able to see the virtual drives that Wine creates.

---

