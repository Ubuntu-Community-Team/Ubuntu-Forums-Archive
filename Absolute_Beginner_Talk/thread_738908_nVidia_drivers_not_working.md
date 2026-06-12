---
title: "nVidia drivers not working?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by ematr1x on 2008-03-29
Hey I am very new to linux and I am using ubuntu 7.10 and it doesnt work very well When I enable my nVidia graphics driver on it and restart the compit loads up but the screen is just black Icant see anything.  So i reinstall it and it works fine.

 Also I cant do some of the things without the updates also when i try and load pigean it goes to the menu bar and says its loading but  nothing comes up 

When I download somthing in firefox and try and open it it says unreconized even when i download stuff for ubuntu it still says unable to unpack i was wondering if anyone could help me with these problems??

---

### Post by overdrank on 2008-03-29
> **ematr1x said:**
> Hey I am very new to linux and I am using ubuntu 7.10 and it doesnt work very well When I enable my nVidia graphics driver on it and restart the compit loads up but the screen is just black Icant see anything.  So i reinstall it and it works fine.

 Also I cant do some of the things without the updates also when i try and load pigean it goes to the menu bar and says its loading but  nothing comes up 

When I download somthing in firefox and try and open it it says unreconized even when i download stuff for ubuntu it still says unable to unpack i was wondering if anyone could help me with these problems??

Hi and welcome, please do not make multiple threads on the same subject
[http://ubuntuforums.org/showthread.php?t=738904](http://ubuntuforums.org/showthread.php?t=738904)
What is the model of the nvidia graphics card? What are you trying to install? Did you check the cd for errors before installing?

---

### Post by ematr1x on 2008-03-29
all i did wus enable the nivida driver i have a 7900 gtx and it doesnt give me an error it says it works fine Sorry for multiple posting i am just frusterated but it says its installed and it needs to restart when i restart it loads but theres no screen

---

### Post by overdrank on 2008-03-29
> **ematr1x said:**
> all i did wus enable the nivida driver i have a 7900 gtx and it doesnt give me an error it says it works fine Sorry for multiple posting i am just frusterated but it says its installed and it needs to restart when i restart it loads but theres no screen

Hi and you may look at Envy to install your graphics drivers
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can try and i when you reach the login screen or the blank screen, use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!
Edit did you install Ubuntu with alternate cd?

---

### Post by ematr1x on 2008-03-29
umm  i dont think so i just downloaded ubuntu and burnt it to a cd

---

### Post by ematr1x on 2008-03-29
also when i am in pigeon and how i open it up it says i am logged in i just cant open it or anything? plus it wont let me enable the video driver without going blank screen?

---

### Post by hunter_te on 2008-03-29
Have u enabled all the repositories and then updated ubuntu? 
If yes, download envy and it will install the driver for ur card automatically.

If no, then go to System>Administration>Software sources and enable repositories.

---

### Post by ematr1x on 2008-03-29
yea its updated and i followed wut you said didnt ask me questions but it also didnt go to the blank screen and its still not enabled and as with pigion yes its the instnat messaging thing it logged me in but i cant open it anywhere?? and as for the enable respitories and update i updated but i dont know what respitories are

---

### Post by overdrank on 2008-03-29
> **ematr1x said:**
> yea its updated and i followed wut you said didnt ask me questions but it also didnt go to the blank screen and its still not enabled and as with pigion yes its the instnat messaging thing it logged me in but i cant open it anywhere?? and as for the enable respitories and update i updated but i dont know what respitories are

Ok on the nvidia drivers you can use this command in the terminal to see what driver is being used in the xorg
```
cat < /etc/X11/xorg.conf |grep Driver
```
Example
	Driver		"kbd"
	Driver		"vmmouse"
	Driver		"nvidia"
The terminal is located under applications, accessories.
As for pidgin, if you are logged in, I don't understand what you mean open it.
The repositories are explained better here
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by ematr1x on 2008-03-29
by open it i mean like i cant open the menu to talk to my friends i cant open th epart to choose aim or msn it just wont open it logs in then its like it doesnt even load at all

as for the driver thing it says
Driver "kbd"
Driver "mouse"
Driver "wacom"
Driver "wacom"
Driver "wacom"
Driver "nv"

and thats it

---

