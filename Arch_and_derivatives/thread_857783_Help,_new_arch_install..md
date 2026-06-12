---
title: "Help, new arch install."
date: 2008-07-12
forum: Arch and derivatives
---

### Post by gr1Mo on 2008-07-12
New arch install :guitar:.

---

### Post by YodaMstr on 2008-07-12
The kernel will install when you select the packages to install.  It's in the base packages, I believe.  I could be wrong about it all, but I know that the kernel will install if you just follow the beginner's guide.  X doesn't come with a base Arch install, so you'll have to download, install, and configure it yourself.  Then you should be able to startx just fine.

---

### Post by gr1Mo on 2008-07-12
> **YodaMstr said:**
> The kernel will install when you select the packages to install.  It's in the base packages, I believe.  I could be wrong about it all, but I know that the kernel will install if you just follow the beginner's guide.  X doesn't come with a base Arch install, so you'll have to download, install, and configure it yourself.  Then you should be able to startx just fine.

I think you may be correct, but as far as downloading and installing X, how should I go about doing that?

---

### Post by Dr Small on 2008-07-12
> **gr1Mo said:**
> I think you may be correct, but as far as downloading and installing X, how should I go about doing that?
Finish setting up Arch, boot to Arch, setup the network and then install Xorg. It is all very detailed and explanitory in the Arch Beginner's Guide.

Dr Small

---

### Post by gr1Mo on 2008-07-12
It's already installed, I'm logged in to root,but when ever i try to use the commands it tells me,error " "not found in sync db.

---

### Post by Dr Small on 2008-07-12
You need to sync pacman then.
```
pacman -Sy
```

---

### Post by gr1Mo on 2008-07-13
1234

---

### Post by mips on 2008-07-13
Try CTRL-ALT-BACKSPACE to get to a terminal.

Make sure you have the correct video driver installed and follow this to the letter: [http://wiki.archlinux.org/index.php/Beginners_Guide#Part_II:_Install_X_and_configure_ALSA](http://wiki.archlinux.org/index.php/Beginners_Guide#Part_II:_Install_X_and_configure_ALSA)

---

### Post by Rollinco on 2008-07-14
CTRL-ALT-BACKSPACE will log you out of X. Try CTRL-ALT-F1 or F2.

---

### Post by kvk on 2008-07-14
I'm having problems running X as well, primarily from the inability to correctly define the video driver. The /var/log/Xorg.0.log file produces two (EE) errors, one from the inability to load module (1) [module (1) is never defined or identified], and the second from Arch not being able to find the defined video driver. I've tried both selecting the Intel open-source driver from the list presented in the Arch Beginners Guide, or simply using the VESA driver, with the same results.

I've also run hwd -xa for auto detection, creation and replacement of the /etc/X11/xorg.conf file, which produces even more errors.

All efforts produce the final termination "No screens found", as usual.

The machine is a Gateway 200 ARC, using the Intel 82855GM integrated chipset.

THIS time, though, I am not forgetting to preface file paths with a text editor for modifying them. :)

---

### Post by MisfitI38 on 2008-07-14
> **kvk said:**
> I'm having problems running X as well, primarily from the inability to correctly define the video driver. The /var/log/Xorg.0.log file produces two (EE) errors, one from the inability to load module (1) [module (1) is never defined or identified], and the second from Arch not being able to find the defined video driver. I've tried both selecting the Intel open-source driver from the list presented in the Arch Beginners Guide, or simply using the VESA driver, with the same results.

I've also run hwd -xa for auto detection, creation and replacement of the /etc/X11/xorg.conf file, which produces even more errors.

All efforts produce the final termination "No screens found", as usual.

The machine is a Gateway 200 ARC, using the Intel 82855GM integrated chipset.

THIS time, though, I am not forgetting to preface file paths with a text editor for modifying them. :)\
Have you installed the driver and xorg with pacman, and then specified the chosen driver in the device section of xorg.conf?

---

### Post by kvk on 2008-07-14
Yes indeed! I'm thinking the whole thing has to do with the machine being relatively old and not one of Gateway's more successful models, so the hardware support might not be the most reliable in terms of what's listed.

I'll play around with it some more this evening and maybe try some different drivers.

---

### Post by kvk on 2008-07-15
So I didn't have any luck searching for the problem.

SO...I installed Puppy, used the auto configuration in that to generate a /etc/X11/xorg/conf file, and then checked it to see what was listed in there. When I get a minute, I'll use that information in the Arch configuration file and see if that functions.

---

### Post by crimesaucer on 2008-07-16
> **gr1Mo said:**
> It's already installed, I'm logged in to root,but when ever i try to use the commands it tells me,error " "not found in sync db.

Did you install from cd?

If you did, you might of installed the base packages correctly, but maybe your eth connection isn't recognized, so you can't "pacman -Syu" to finish the install. 

Check to see if your eth is connected:

```
ifconfig
```


I tried to install on a brand new Acer laptop a week ago, and the ethernet connection wouldn't get recognized and I did not know what module to load. I would get a similar error when my /etc/pacman.d/mirrorslist was not connected to an eth0 connection when I tried to "pacman -Syu". 


It did recognize the atheros wireless when I tried to install using the ftp method, but I had no wifi stream to finish the install from so I never got to see how Arch worked on the acer.  


Anyway, I didn't like the acer too much so I returned it and got a HP pavilion dv9920us, it recognized my AMD forcedeth ethernet perfectly durring a ftp install... but now there is no way to get my bcm4322 pre-n to work... 


... unless somebody has a windows xp64 driver for me? (bcmwl564.sys)... 


So now I'm gonna be stuck using Vista when I leave the home and have to use wireless.


I'm sure I could make the bcm432b card work with ndiswrapper if I could locate the correct xp driver and INF file from a similar HP Pavilion DV9920us using the 64bit Xp profession instead of Vista 64... (vista drivers don't work, and the b43 hasn't got to the 802.11n cards yet)

---

