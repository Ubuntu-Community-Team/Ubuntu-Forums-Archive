---
title: "Permissions"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Audrokit on 2007-03-25
I installed Ubuntu 6,1 on my lap top and it ran over an windows XP install - I wanted to drag some files off the drive however, It's saying I dont have permissions as I'm not the owner!!!  I went to the user profiles and I am set as the administrator...?? I need to remove the files urgently.. How can I ensure I am the administrator?

---

### Post by dacool25 on 2007-03-25
go to the terminal and type gksudo nautilus.  After that enter your password and you'll be able to navigate to your hard drive.  Best of luck.

---

### Post by g3k0 on 2007-03-25
use gksudo nautilius if you want to have a root window.

If you are doing it from command line you can use sudo before it.

If you want to change permissions of a file you need to do a sudo chmod or change it by right clicking with gksudo nautilus

!!! Edit:  ack you beat me to it. Heres 1000 free points.

---

### Post by Audrokit on 2007-03-25
why did the install ask for user name - then install that user without permissions?  i created the password for that user... so what's the user for the root?

---

### Post by ecko_blue on 2007-03-25
Ubuntu disables root login as a default as a security feature. It's quite frustrating for someone like me (or us) who have just come to linux from WinXP where we have the control to do anything. If you want to change anything remotely significant via the window you have to use the terminal (Applications>Accessories>Terminal) and type in 'gksudo nautilus' like said above.

sudo for terminal commands, and gksudo for launching apps from the terminal give you temporary administrator access to make changes.

There is a method to login as root in ubuntu, but it isn't recommended.

---

