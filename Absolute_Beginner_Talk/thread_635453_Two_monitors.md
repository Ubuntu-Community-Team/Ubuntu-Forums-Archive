---
title: "Two monitors?"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by AJLChase on 2007-12-08
Hi, I just installed Ubuntu and have managed to get the accelerated graphics running just fine. But, I am not able to have both of my monitors displaying at the same time. In fact, my other monitor has seemed to fall asleep. Are there any tutorials on how to get two side by side displays working? thanks!

---

### Post by rsambuca on 2007-12-08
What video card, and what drivers are you using?

---

### Post by AJLChase on 2007-12-08
Hi, thanks for the fast response! I have a Geforce Evga 8800gts. And I am not sure what drivers I am using as I installed ubuntu about 30 minutes ago and havent done anything with downloading. I am currently in the middle of downloading updates. And that is all I know for right now.

---

### Post by rsambuca on 2007-12-08
You will have to manually install the latest beta driver from nvidia with that card.  Instructions are on the nvidia website where you download the driver from.  After you have it installed, then you want to install nvidia-settings to configure your monitors.

---

### Post by jrharvey on 2007-12-08
Ok this is how I do it.... Download nvidia-settings from synaptic package manager. After that type in "sudo nvidia-settings" in your terminal. This may also be in applications/system tools. In the window click on xserver display configuration. You should be able to do whatever you need to from there. I use twin view over separate xscreen because it still works and it is faster because you dont have two copletely separate xscreens. If  you like your settings then just hit "save to X configuration file"

---

### Post by Presto123 on 2007-12-08
> **jrharvey said:**
> Ok this is how I do it.... Download nvidia-settings from synaptic package manager. After that type in "sudo nvidia-settings" in your terminal. This may also be in applications/system tools. In the window click on xserver display configuration. You should be able to do whatever you need to from there. I use twin view over separate xscreen because it still works and it is faster because you dont have two copletely separate xscreens. If  you like your settings then just hit "save to X configuration file"

The easiest way I found it is to do it through the Add/Remove under Applications and search Nvidia. You could probably use the "New" driver with that kind of card. Then go into "Restricted Drivers Manager" under "System" then "Administration" and enable the driver and restart. Create a launcher on the desktop (Right click and "Create Launcher") and use a name you want then the code is as follows:

```
gksudo nvidia-settings
```

You can enable the other device and make sure to "Save to Xconfiguration File" then restart your computer and see if it works right.

---

### Post by rsambuca on 2007-12-08
I don't think the nvidia-glx-new drivers work well the the 8800.  I am pretty sure you have to install the beta driver from nvidia.

---

### Post by Presto123 on 2007-12-08
> **rsambuca said:**
> I don't think the nvidia-glx-new drivers work well the the 8800.  I am pretty sure you have to install the beta driver from nvidia.

You're probably right, I'm running Feisty and the "Binary" works just fine on a 6200.

To the person in need of help: I must add that you don't HAVE to create a launcher. I just found it easier when I had two monitors running. I gave one up for a while b/c someone needed the monitor and it was soo much easier to work with things without having to remember the code.

---

### Post by AJLChase on 2007-12-08
Well, when I try to download NVIDIA-Linux-x86-100.14.19-pkg1.run it says theres an error and wont let me download it?

---

### Post by rsambuca on 2007-12-08
> **Presto123 said:**
> You're probably right, I'm running Feisty and the "Binary" works just fine on a 6200.

To the person in need of help: I must add that you don't HAVE to create a launcher. I just found it easier when I had two monitors running. I gave one up for a while b/c someone needed the monitor and it was soo much easier to work with things without having to remember the code.

I wrote 'beta' because I meant 'beta'.

[http://www.nvnews.net/vbulletin/showthread.php?t=102509](http://www.nvnews.net/vbulletin/showthread.php?t=102509)

---

### Post by Presto123 on 2007-12-08
Lol. I'm not correcting you, I write things like that to differentiate between the three available.

---

### Post by AJLChase on 2007-12-08
I get this when trying to download XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 4:   var mimeLiteral = gRDF.GetLiteral(aValueString);
---^

---

### Post by Presto123 on 2007-12-08
Hrm...Someone else will have to handle that one. I can't remember seeing this problem.

---

### Post by rsambuca on 2007-12-08
> **AJLChase said:**
> I get this when trying to download XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1, Column 4:   var mimeLiteral = gRDF.GetLiteral(aValueString);
---^

If you are going to install that driver, just do it from the Restricted Drivers Manager.  It is the same one.  I am not sure that one works with your card, although it can't hurt to try it.  Go to System -> Administration -> Restricted Drivers Manager.  It should walk you through the installation.

---

### Post by AJLChase on 2007-12-08
Ok, the only ones i was able to install that didn't mess iwht my screens resolution was nvidia-glx-new and when I try to use synaptic to install the nvidia settings it can only do this by removing the latest drivers. Ideas :D

---

### Post by rsambuca on 2007-12-08
You don't need to install nvidia-settings (that is for the legacy drivers).  I know it is a little confusing, but in this case you just want to run the command nvidia-settings with gksudo to get permissions.

gksudo nvidia-settings

---

### Post by AJLChase on 2007-12-08
Sweet, any advice as to what to use as the settings. My Sony HMD-A240 is currently disabled. What would be the next step to get this bad boy running? My only worry is that if and when I do restart...my ubuntu wont work..its happened to me before and I never know how to get into the GUI without reinstalling :(

---

### Post by rsambuca on 2007-12-08
If the driver doesn't work after rebooting, you can fix it via the command line.  Write down this command:

sudo nano /etc/X11/xorg.conf

This will allow you to change the driver back to 'nv' from 'nvidia' in the "Device" section.  Just remember that linux filenames are case-sensitive, so X11 is different from x11 (you want to use a capital X and those are ones, not lower case L's).  Scroll through the xorg.conf to the Device section, change the driver from nvidia to nv, and then press Control-O to save it, and then Control-X to close.

---

### Post by AJLChase on 2007-12-08
Awesome, im trying now to insall WoW through Wine..and all is going well so far, so once that's all done Ill reboot linux to see how I come out. And hopefully I fair better then the previous times. You must know what you're doing with all this because you've responded in rapid fire timing ;)

---

### Post by rsambuca on 2007-12-08
Actually I have no idea what I am doing.  I just have time to kill and can type pretty fast. :)

Good luck, but like I said, I don't think people are having a ton of success with that card and driver combo.

---

### Post by jrharvey on 2007-12-09
now what is the difference between using "gksuko" and "sudo"? I have always used "sudo nvidia-settings" and it seems to work. Is there a difference?

---

### Post by rsambuca on 2007-12-09
> **jrharvey said:**
> now what is the difference between using "gksuko" and "sudo"? I have always used "sudo nvidia-settings" and it seems to work. Is there a difference?

Basically, gksudo (or gksu) should be used anytime you run a graphical environment program that requires root permissions.  Although just using sudo will work most of the time, there are a few instances where it can actually mess up the permissions of resulting files and make your system unstable.  Therefore, as a general rule of practice, if you require root permission in a program that does not run inside the terminal, then use gksudo.  If it is just inside the terminal window, then use sudo.

---

