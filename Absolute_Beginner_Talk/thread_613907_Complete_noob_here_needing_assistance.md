---
title: "Complete noob here needing assistance"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Jmannumber7 on 2007-11-15
Hey guys, I just DL'd Ubuntu 7.10 and burned it onto a disc with MagicIso. After that, I partitioned my harddrive in windows vista giving me 22 GB to install ubuntu without effecting windows on the C:\ drive. After I partitioned that, I took 1.5 GB for the swap so ubuntu would run smoothly. Now Im running vista and ubuntu and I just choose which one I want to boot up when my machine starts up. I have everything installed perfectly with ubuntu and my account created and such, but I was just wondering, on the root account or system administrator account, everytime I try and login using the user name root and the password I specified for it it says im not allowed to login as system administrator from this screen (the main login screen at boot) but I can login with my regular account. How do I login to the root account and what is the difference between the root account and my account im on now? Thanks in advance for your guys help, im reading all about linux and commands and such right now, so hopefully ill have a better understanding of it soon!

---

### Post by overdrank on 2007-11-15
> **Jmannumber7 said:**
> Hey guys, I just DL'd Ubuntu 7.10 and burned it onto a disc with MagicIso. After that, I partitioned my harddrive in windows vista giving me 22 GB to install ubuntu without effecting windows on the C:\ drive. After I partitioned that, I took 1.5 GB for the swap so ubuntu would run smoothly. Now Im running vista and ubuntu and I just choose which one I want to boot up when my machine starts up. I have everything installed perfectly with ubuntu and my account created and such, but I was just wondering, on the root account or system administrator account, everytime I try and login using the user name root and the password I specified for it it says im not allowed to login as system administrator from this screen (the main login screen at boot) but I can login with my regular account. How do I login to the root account and what is the difference between the root account and my account im on now? Thanks in advance for your guys help, im reading all about linux and commands and such right now, so hopefully ill have a better understanding of it soon!

HI and welcome, this link may help
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mjitkop on 2007-11-15
You do not need to login as root at the first login screen. Just login with your username on your regular account. Later if you want to run some commands that require root access, a window will pop up asking you for your password (the same as your regular account password.) You will then have root access for a certain amount of time (I forgot how long.) :)

---

### Post by Paul820 on 2007-11-15
This will explain about the root and the way it works [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Jadd on 2007-11-15
Hi Jmannumber7.
I'm still learning Ubuntu myself, but I've found that I've never needed to log in as root. Your user has administrative powers, so you can do most of the root can do by providing a password: example: updating your system by clicking System, Administration, Update Manager, Install Updates.
On the command line type sudo before every command to get administrator privileges. If you're about to launch a graphical program, use gksu (or gksudo) instead. Example: press alt-f2, type gksu nautilus and click run to get an 'explorer' with administrator privileges.
Here's an excellent page on the subject: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Jmannumber7 on 2007-11-15
Thanks everyone! That helped me out a ton, thanks for the helpful replies and no flaming what so ever :)

---

### Post by Jadd on 2007-11-15
Haha, all three of us answered in less than three minutes, the Ubuntu community rocks!

---

