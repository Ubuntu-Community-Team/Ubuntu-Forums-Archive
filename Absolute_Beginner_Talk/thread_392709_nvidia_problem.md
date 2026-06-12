---
title: "nvidia problem"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by serge2k on 2007-03-24
I wanted to install beryl but I found out I needed to get the nvidia drivers first.

So I tried using this guide [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html") but when I restarted it gave me an error about no screen and went into the terminal.

Does anyone know how to fix it or do you need more information (and if so, what?)

---

### Post by kepos on 2007-03-24
same thing happaned to me (few post lower). havent found solution jet. Which graphic card do you have?

if you have backuped you xorg.conf file than there should be no problem. Look if there is any backup file in /etc/X11/ and resotre it

---

### Post by r4ik on 2007-03-24
sudo dpkg-reconfigure xserver-xorg

Follow the defaults and set you're graphics to nv
If you have a visual you could try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---

### Post by serge2k on 2007-03-24
I got it working by using the dpkg-reconfigure xserver-xorg with nv and then I downloaded envy but the nvidia drivers still don't work.

I have a GeForce Go7300

---

