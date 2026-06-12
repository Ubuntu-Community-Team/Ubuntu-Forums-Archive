---
title: "Nvidia driver installation"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Jacobson on 2006-12-23
Hello, new user here

I have installed ubuntu 6.10 onto a new pc of mine with an Nvidia 6300gt. 
I feel like i have tried as many possible ways to get the nvidia drivers installed.. searched this forum, google.. etc it doesnt appear to be working, I am probably doing something wrong.

Could somebody point me in the direction of some installation instructions that would be suitable?  The more comprehensive the better. 

thank you! :D

---

### Post by pissedoffdude on 2006-12-23
> **Jacobson said:**
> Hello, new user here

I have installed ubuntu 6.10 onto a new pc of mine with an Nvidia 6300gt. 
I feel like i have tried as many possible ways to get the nvidia drivers installed.. searched this forum, google.. etc it doesnt appear to be working, I am probably doing something wrong.

Could somebody point me in the direction of some installation instructions that would be suitable?  The more comprehensive the better. 

thank you! :D
you should be able to install the nvidia drivers using automatix

---

### Post by r4ik on 2006-12-23
Try,

[http://albertomilone.com/guides.html](http://albertomilone.com/guides.html)

Good luck !

---

### Post by Jacobson on 2006-12-23
@ pissedoffdude 
it worked! and oh so easily! thankyou!

@ r4ik
thanks for the link, lots of usefull info :-D

---

### Post by venik212 on 2006-12-23
What is Automatix?

---

### Post by Cariboo1938 on 2006-12-24
> **pissedoffdude said:**
> you should be able to install the nvidia drivers using automatixPlease, could give further details how to proceed. Does it work for Edgy-AMD64?

---

### Post by logos34 on 2006-12-25
add this to your /etc/apt/sources.lst:

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

or add to the third party repositories in your package manager.

$ sudo apt-get install automatix2

or look for automatix2 in the package manager

---

### Post by iPirates on 2006-12-25
Is EasyUbuntu as good as Automatix2?  Do they essentially do the same thing?

---

### Post by Malta paul on 2006-12-25
Hi Ipirates,
Yes Easyubuntu is very good, but I prefer Automatix2 because it has more choice of programmes and perhaps more important for me, is its ability to uninstall its programmes if you wish. ;)

---

### Post by iPirates on 2006-12-26
Good to know... :)

---

### Post by venik212 on 2006-12-27
I used Automatix2 to install the Nvidia stuff, and it went smoothly.  However, there still seems to be no way to get the full resolution of the old Nvidia card I use (1280X1024) which XP on the same machine gets easily.  The maximum resolution I get is 1024X768.  HELP, please!

---

### Post by JayTee on 2006-12-27
try running this from the command line,
gksu nvidia-settings and then click on X Server Display Configuration. Set the settings to the resolution and refresh rate you want and click apply. If the settings you chose work ok then choose Save to X configuration file. I found I had to run this with gksu (graphical sudo) or the changes would not be saved to my /etc/X11/xorg.conf file.
Hope this helps.

---

### Post by venik212 on 2006-12-27
I tried that, but:
1) There is no option X server display settings
2) I could not find resolution settings anywhere, except in the System/preferences/screen resolution, where the option I know the card is capable of (1280X1024) is not available.

Sounds like Ubuntu is unable to give me the full use of the card...

---

### Post by venik212 on 2006-12-28
Finally, with the help of the nice ENVY script from Alberto, I wrestled the NVIDIA driver to the ground, and now my resolution is the same as on XP.

---

