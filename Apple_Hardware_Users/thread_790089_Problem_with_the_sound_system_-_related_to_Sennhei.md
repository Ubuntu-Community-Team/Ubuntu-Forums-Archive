---
title: "Problem with the sound system - related to Sennheiser headset."
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by khelben1979 on 2008-05-11
Hello.

When I insert my Sennheiser USB headset in the USB port and then reboot the Debian Etch system, the system starts to use the Sennheiser as the default sound system. No problem so far.

Now comes the problem: When I remove the Sennheiser I get no sound and the cpu get up to 100% constant. When I restart the X server, the X server gives me the message that the sound server was unable to initialize correct and I still get no sound.

So everytime I want to switch between the PowerMac Screamer sound output and between the Sennheiser I reboot the machine. I don't experience this as very effective and I don't like at all. I want to get rid of this behaviour and start using Linux the way it was meant to be used, not like a Windows system where one has to reboot all the time (not even Windows reacts this bad in this case).

Need your support! What shall I do?

(This affects both my Gnome and KDE enviroment)

---

### Post by russo.mic on 2008-05-11
Well,  I would first of all keep in mind that debian etch isn't ubuntu,

I would try restarting alsa as a troubleshooting step..

sudo /etc/init.d/alsa-utils restart

Post your results here.

Russo

---

### Post by khelben1979 on 2008-05-11
> **russo.mic said:**
> Well,  I would first of all keep in mind that debian etch isn't ubuntu,

I would try restarting alsa as a troubleshooting step..

sudo /etc/init.d/alsa-utils restart

Post your results here.

Russo

I've tried a lot of things now and nothing has helped. I installed that alsa-utils package since I didn't had it before and configured the sound system with alsaconf.

I would like to be able to switch between the inbuilt speaker system and my Sennheiser USB headset, that would be optimal.

So.. need more support.

---

### Post by cyberdork33 on 2008-05-11
Since this is likely not a Mac-specific issue, I would suggest asking for help from those with a bit more knowledge about the tech aspects of ALSA in Debian.

---

### Post by scrondo on 2008-11-08
check this out ---->  [http://ph.ubuntuforums.com/showthread.php?t=954325&nojs=1#goto_threadtools](http://ph.ubuntuforums.com/showthread.php?t=954325&nojs=1#goto_threadtools)

I got a sennheiser usb headset too, and it worked great for me

---

### Post by khelben1979 on 2008-11-09
If I have the Sennheiser headset installed when booting the system, then I can see both devices and switch between them using KMix, but the system can never go back to the inbuilt speaker system without me rebooting the system.

You mean that the Asoundconf-gtk program solved this problem?

---

