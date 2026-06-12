---
title: "Blank Screen"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by hfashina@hotmail.com on 2006-04-23
This is my first time trying to use Linux.  I've installed it on an older computer.  It goes through the boot process fine, but then goes to a blank screen.  I assume its a video driver problem.

I am using a pentium II 233 and a S3 Trio 64V2  video card.  Can someone direct to where and how I could load a driver for that or as to what else the problem could be

Thanks

---

### Post by dermotti on 2006-04-23
Can you try pressing **cntrl + alt + F3** at teh same time and see if you get a login prompt?

---

### Post by hfashina@hotmail.com on 2006-04-23
I just get a flashing cursor

---

### Post by hfashina@hotmail.com on 2006-04-23
Oh wait,  I tried it again and I got to the login prompt and have logged in.

Thanks for the help

---

### Post by hfashina@hotmail.com on 2006-04-23
How do I get the desktop though?

---

### Post by mcmillan on 2006-04-23
try typing startx. I have a feeling it won't work, but it will probably give some errors that might be some help.

---

### Post by hfashina@hotmail.com on 2006-04-23
It said

Fatal server error:
Server already active for display 0

etc etc etc

---

### Post by dermotti on 2006-04-23
run  **sudo dpkg-reconfigure xserver-xorg**  and select **vesa** as your driver

Then run

**ps -e | grep gdm**


you should see something like

5678 gdm

then run **sudo kill 5678 **(5678 could be any number on yours system)

then run

**gdm**
__________

---

### Post by hfashina@hotmail.com on 2006-04-23
after I "sudo kill" the number, it goes to a flashing cursor.  I don't have the opportunity to enter "gdm"

---

### Post by hfashina@hotmail.com on 2006-04-23
after restarting I was able to get through the process, but when i typed **gdm** it said "Only root wants to run gdm".   How do I log in as root, I don't recall setting a root password or anything when i installed ubuntu

---

### Post by mcmillan on 2006-04-23
use sudo gdm, then use the user password

---

### Post by hfashina@hotmail.com on 2006-04-23
I get a blue screen that says:  "Failed to start the X server" etc etc

---

### Post by vivmk2000 on 2006-05-09
Hi,

I am facing a similar problem wherein X and gdm does not start, i would like to know on what basis is the driver selected?
I have a p4, would changing the driver solve the problem I have faced?

Regards,
V.M.K

---

### Post by ProjectGod on 2006-05-09
sorry for the topical digression. just wanted to test out my avartar! 
googoo!

:mrgreen:

---

