---
title: "Breakthrough! I'm getting closer! Help still needed"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-03-23
Hey, I've been trying to install my usb wireless adaptor, I've finally managed to get Windows Wireless Drivers to appear in System>Admin (Wahey!) Now I opened it and there's no hardware present. I dragged and dropped all the .inf files that were on my modem install cd (I had put them in a folder on my desktop) and none of them work - still no hardware present.  If I run ndiswrapper I get this:

clare@linuxubuntu:~$ ndiswrapper -l
Installed ndis drivers:
bluedsl invalid driver!
{driver}        invalid driver!
drivername      invalid driver!
dw200-0a5c      invalid driver!
dw200-0f4f      invalid driver!
inventelgateway invalid driver!
rescuedrv       driver present
clare@linuxubuntu:~$

Does anyone have any ideas? I'm sure I'm getting close!
Thanks for all the help so far.

Ooops, I forgot to say I went through the install new driver process with all the inf files. No bleeping hardware..

---

### Post by stupidel on 2006-03-23
I'm pretty new to this, but i did just go through a week of constant reimaging to get my wireless card on my hp laptop working.  The first thing to check is that if you are using a 64 bit version of ubuntu that you are using 64bit drivers.  Second remove all the invalid drivers with the sudo ndiswrapper -e <driver name> command.  If you don't have too much on your system right now, i've noticed ubuntu gets cloged up easily, try wiping and trying again.  now that you know how to get to the point you are it makes it much easier and working with a clean system definitly helps.

Again i'm new, this may or may not be of help but this is what worked for me. 

good luck:)

---

### Post by clareb on 2006-03-23
Hey, thanks for the input. I'm not sure how to check if the drivers are 64bit. I want to download drivers from the sourceforge page but I can't find my chipset and they don't even have inventel listed there but I'm googling to try and find solutions. I need luck.;)

---

