---
title: "Failed to Start the X-Server (your graphica interface)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by grimerking on 2007-01-21
I'm a total beginner with Ubuntu. I have download the bootable CD and am trying to run it for the first time. I have verified the CD is OK and also checked my RAM. 

When the disk boots, it takes me to the main menu. I set my graphics to 1280x1024 16bit (I have also tried 32bit and safe mode)

I then select 'boot/install' and the loading screen appears. After about 30 seconds this disappears and there is a black screen with a flashing white cursor in the top left. After about 20 seconds this disappears and an error window appears. The message states: 

"Failed to start the X-Server (your graphical interace). It is likely that it is not set up correctly. Would you like to see the X Server output to diagnose the problem?"

If I select yes, it brings up a page of gobbledegook

When I press 'enter' another message appears: 

'The X Server is now disabled. Restart GDM when it is configured correctly.'

___________________

What is happening and how do I fix it? My system specs are: 

Opteron 144 @ 2.44GHz
1GB RAM @ 3-3-3-8 1T
Radeon X850XT
Soundblaster 5.1 Digital
Compro DVB-T300 TV Card
2 x IDE HDD
1 x SATA HDD
ASROCK 939 Dual SATA MB
DVDRW

Windows is rock solid stable. RAM is testing fine. CD is testing fine. 

Any ideas? 

Thanks, 

Rob

---

### Post by arochester on 2007-01-21
From the command line use the command >  sudo dpkg-reconfigure xserver-xorg
. This will start a text wizard which should allow you to reconfigure X. If you do not know the answer to any questions go with the default answer.

---

### Post by r4ik on 2007-01-21
When finished you could get youre driver here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

good luck !

---

### Post by grimerking on 2007-01-21
Thanks for the reply, but how do I get to the command line? At what point in the boot process do I access it? Sorry to be such a noob. I'm pretty sharp with windows and networks, but I've never used Linux and I haven't programmed since the BBC Basic. 

Thanks, 

Rob

---

### Post by jbayone on 2007-01-21
You may also want to try a lower resolution if you're having this problem with the live CD.

---

### Post by Tenicus on 2007-01-21
> **grimerking said:**
> Thanks for the reply, but how do I get to the command line? At what point in the boot process do I access it? Sorry to be such a noob. I'm pretty sharp with windows and networks, but I've never used Linux and I haven't programmed since the BBC Basic. 

Thanks, 

Rob

CTRL+ALT+F1 should do it

---

### Post by grimerking on 2007-01-29
I've been a bit busy and have only just had a chance to try the suggested fixes. 

I got into the graphical interface and worked through the questions - selected my card, colour depth, etc. 

At the end, it said it was writing the new values to disk and then returned me to the command line. How do I get it to boot from the command line? 

Thanks, 

Rob

---

### Post by aktiwers on 2007-01-29
to start your GUI again type:
```
startx
```

---

### Post by grimerking on 2007-01-29
Thanks

---

### Post by glabouni on 2007-01-29
try a lower resolution of the default resolution from the boot menu, to check if this fixes your problem.
you' ll still be able to change it afterwards.

---

### Post by grimerking on 2007-01-29
I've tried a few different combinations of resolutions and other settings. When I attempt to boot using the startx command, I get an error message: 

Fatal Server Error: 
No Screens Found.
X10: fatal IO error 104 (connection reset by peer) on xserver ":0.0" after 0 requests (0 known processed) with 0 events remaining. 

Any ideas?

---

### Post by grimerking on 2007-01-29
Does anybody know what could be causing this?

---

### Post by jbayone on 2007-01-29
When you go through sudo dpkg-reconfigure xserver-xorg, try to de-select the higher resolutions.  It's one of the options in the monitor setup.

---

### Post by Muphin Man on 2007-01-29
You have the EXACT same problem that I have...

I think it might be how when you finish all the questions in the XServer config it brings you back to the command line. The only problem is that I don't think it's saving your settings, so when you startx, it's still the same. This is me guessing though so who knows...

I'm a Linux noob too and I can't figure this out! Can someone help both of us please!?

---

### Post by grimerking on 2007-01-30
I tried using the most basic graphics settings (800x600, 16bit, 60 Htz). 

I deselected all the more advanced settings and chose the defaults for everything else. It still won't boot into Ubuntu. 

If anybody has managed to fix this problem, please let me know. Otherwise I guess I'll just have to try Suse instead. 

Thanks, 

Rob

---

### Post by wowshailen on 2008-02-17
I am using Fedora 8 and got the same problem, which brought me here.

I however, managed to correct the bug, by reinstalling Xorg-server from the non-Gui mode.

I mounted the DVD,
mkdir  /media/dvd
mount /dev/cdrom /media/dvd

Then i searched for the Xorg-server installation file (which has an rpm extension, unlike .deb in Ubuntu)

Then i installed the Xorg-Sever-x.x.x.rpm:
rpm -ivh Xorg-Sever-x.x.x.rpm

When i rebooted my machine , my GUI was okay..

I hope that can help you for Ubuntu, though the syntax is a lil bit different..

Good Luck :)

---

