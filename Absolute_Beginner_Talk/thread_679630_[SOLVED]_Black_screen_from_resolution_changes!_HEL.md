---
title: "[SOLVED] Black screen from resolution changes! HELP!"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by TygerTung on 2008-01-27
When I installed ubuntu it set my resolution to 1280x1024 pixels with a refresh rate of 60 Hz. This is a bit flickery for my liking on my  Phillips 107S5 CRT monitor, so I tried to change to a lower resolution with a higher refresh rate, but when I changed it it told me that I had to restart the computer to make the changes and when I did, it just came up with a black screen after the loading screen! How can I change it back? Can I use the recovery console or somthing?

Thanks,

Sam

---

### Post by DamagePlan on 2008-01-27
Try rebooting, then

-Boot into recovery
- once booted type: sudo dpkg-reconfigure -phigh xserver-xorg 
or could be sudo dpkg-reconfigure xserver-xorg
- follow the instructions.
- then type sudo reboot now.

Im new to linux but this is an idea.

---

### Post by xeth_delta on 2008-01-27
Yes it is possible to change it. If you can, access the recovery console and edit the file "/etc/X11/xorg.conf"
First start by making a back-up of the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```
then open the file
```
sudo nano /etc/X11/xorg.conf
```
Look for the section called << Section "Screen">> and the lines starting with Modes. Change them to the resolution you want.

To save the file use Control-O. To exit, Control-X.

Let us know if you need more help.
Xeth

---

### Post by TygerTung on 2008-01-27
Yes I have a problem, I cannot seem to find the file in question!

It tells me that the file I am looking for does not exist or words to that effect.

I manually circumnavigated my way into the  etc directory but I couldn't find the directory x11.

I also couldn't work out how to make the screen pause for a moment when I use the "dir" command to find out the contents of a directory and the contents of that directory exceed the screen size so it just scrolls down and you cannot see what is at the top!

---

### Post by schiznik on 2008-01-27
> **TygerTung said:**
> Yes I have a problem, I cannot seem to find the file in question!

It tells me that the file I am looking for does not exist or words to that effect.

I manually circumnavigated my way into the  etc directory but I couldn't find the directory x11.

I also couldn't work out how to make the screen pause for a moment when I use the "dir" command to find out the contents of a directory and the contents of that directory exceed the screen size so it just scrolls down and you cannot see what is at the top!
The directory is X11 (/etc/X11/xorg.conf) - linux is case sensitive.

To make the screen pause, as dos does with dir /p (i think.. its been a good while), I would run```
ls |less
```This uses a pipe (the key between shift and z on a uk keyboard) to send the output from ls (the linux version of dir) through less, which will allow you to scroll up and down. Push q when you reach the end to return to the prompt.

---

### Post by TygerTung on 2008-01-27
Yeah I tried editing it, and deleted all the modes I didn't want under screen modes and it still just comes up with a black screeen after the splash screen. The problem seems even more serious because it doesn't make the usual logging in sounds either!

I'm begining to think I may have to reinstall.

---

### Post by TygerTung on 2008-01-27
Noone has any ideas?

---

### Post by xeth_delta on 2008-01-27
Did you try what DamagePlan said? By the way, how much space do you have?
Also, what is the outpyt of:
```
cat /var/log/Xorg.0.log | grep -i EE
```
This should show errors in the X11 log

---

### Post by TygerTung on 2008-01-28
Yep I just tried that thing which damage plan suggested and it worked a treat! After asking many questions which I was unsure the answers to I rebooted and it worked fine!

Thanks everyone!

---

