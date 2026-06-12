---
title: "Setting up Wifi with Wifi Radar installed"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-06-05
hey i jus inistalled Wifi Radar, but i just realized my wifi card isn't set up haha  I've been downloading programs in vista then booting to ubuntu and installing them.  I've pretty much got stuff set up how i want but now i'm not 100% sure on setting up the wifi.  

My bluetooth light comes on but no wifi, is there a line of code i can type in the terminal that will set me on a configure path, like the one for the Xserver that i used to set up my graphics?  

Another silly question but when i get the card set up and go into wifi radar will it be just a double click on the signal i wish to use? cause right now i don't have a wireless router i'm using an unprotected signal that's suprisingly fast and works all the time, will i be able to use this in ubuntu with minimal configuration?  

I know the IP adress and all that b y way of ipconfig in command prompt in vista, will i need to copy that info down and enter it in wifi radar?

any help would be greatly appreciated! i look forward to having my dual boot system running 100% soon!  

thanks, Alain

---

### Post by luckyd on 2007-06-05
You could try Gnome- Network-Manager... If you have left everything at the defaults, then you can just simply click on the applet on the panel and choose a wireless network. If that works for you, it would be better than wifi-radar, since it integrates with the system better.

---

### Post by S15_88 on 2007-06-05
ya the thing is though is it doesn't recognize my wifi card so i can't even see any wireless networs availabe, is there a line like     sudo apt-get wifi config?? haha totally jus pulled that out of thin air but ya i need to get the card ready and then worry about connecting to networks.

---

### Post by luckyd on 2007-06-05
What kind of card?

---

### Post by S15_88 on 2007-06-05
Intel Next-Gen

---

### Post by luckyd on 2007-06-05
try this, then reboot > sudo apt-get install linux-restricted-modules-generic

sorry I forgot, once rebooted then> sudo modprobe ipw3945

---

### Post by S15_88 on 2007-06-05
alrighy ill give that a try after i finish dinner, thanks

---

