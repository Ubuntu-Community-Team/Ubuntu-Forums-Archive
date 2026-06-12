---
title: "Some newbie questions"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Th3_uN1Qu3 on 2006-11-09
First of all, thanks for this great piece of software! :)

I'm a total linux newbie and installed Ubuntu after trying the Knoppix live CD. I liked the way Knoppix was done and was really tired of Windoze so i got interested in Linux. Now i've installed Ubuntu Edgy (yes, i somehow managed to install it without screwing my dual-boot Windows 98SE/Tiny Windows 2003 setup, at least not screwing it up yet ;)) and i'm having some issues.

I have a GeForce4 MX440 card and tried installing the linux drivers from the nvidia site following their procedure. They instructed me to type "sh NVIDIA-Linux-x86-1.0-xxxx-pkg1.run" but when i did that it said "sh: Can't open blah blah blah"

I've read somewhere else (the kubuntu forums i believe) that i should try typing "sudo aptitude install nvidia-glx". I did that but it didn't install anything, it said 0 packages something. Meaning it's already installed but it isn't loaded. Now i've understood that i have to edit xorg.conf in /etc/x11/ and change "nv" to "nvidia". I did, but for some reason i can't save it. Has something to do with permissions. There is no "nv" there though, the driver used is "vesa" and my video card is detected as "Generic video card". Also the max resolution available is 1024x768 24bpp @60Hz. My brain tells me that this means my config's seriously messed up.

So any help in editing the xorg.conf file (and saving it)? Or another way of installing the nvidia driver properly?

Another n00bish question: What's the proper way of installing ALSA drivers? Coz i've followed the instructions on their site but with no luck.

Thanks in advance.

---

### Post by ReaderRat on 2006-11-10
To edit your xorg.conf file, first back it up:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bakup
```
Then edit it:
```
sudo gedit /etc/X11/xorg.conf
```
And change what you need to.

---

### Post by confused57 on 2006-11-10
Here's a howto that may help for your nvidia issues:
[http://www.ubuntuforums.org/showthread.php?t=281823&highlight=nvidia](http://www.ubuntuforums.org/showthread.php?t=281823&highlight=nvidia)

---

### Post by digby on 2006-11-10
As a note, to backup your xorg.conf file as mentioned above, you will have to preface the command with sudo.

---

### Post by Th3_uN1Qu3 on 2006-11-10
[quote=ReaderRat]cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bakup[/quote]

With or without sudo. In both cases, i get this: "cp: cannot stat `etc/x11/xorg.conf': No such file or directory.

Also when i try to gedit it, it's locked in read-only and i can't save it. Anymore suggestions?

---

### Post by rlozano on 2006-11-10
> **Th3_uN1Qu3 said:**
> With or without sudo. In both cases, i get this: "cp: cannot stat `etc/x11/xorg.conf': No such file or directory.

Also when i try to gedit it, it's locked in read-only and i can't save it. Anymore suggestions?

it should be:

sudo cp /etc/X11/xorg.conf..... note the / before etc and the CAPITAL X not small x.

and when you edit, use sudo gedit so you can edit the xorg.conf gile because that is owned by the root.

hope this helps.

---

### Post by Th3_uN1Qu3 on 2006-11-10
[quote=rlozano]CAPITAL X[/quote]

Thanks, that worked.

Anyway, i managed to configure my video card and monitor by using "sudo dpkg-reconfigure xserver-xorg" as posted [here](http://www.ubuntuforums.org/showthread.php?t=296779)

Thanks for your help.

Now i'm left with only one unanswered question: How do you install alsa sound drivers properly?

---

### Post by bulldog on 2006-11-10
Did you have a look at synaptic?
Do a search for alsa within synaptic and see what it returns.

Synatptic is found by System--Administration--synaptic

---

### Post by Th3_uN1Qu3 on 2006-11-10
Thanks for the suggestion. I had already used Synaptic to install some stuff (wine :D) but didn't think of searching for ALSA drivers.

I did it now and it appears they're already installed, i have to figure out how to change the driver from OPL to ALSA now.

---

### Post by ReaderRat on 2006-11-10
Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by Th3_uN1Qu3 on 2006-11-10
Thanks. That helped.

My sound is okay now, and i'm starting to get the hang of Ubuntu. I tweaked my HDD to max performance using hdparm (UDMA, finally!!! Hail the linux god!!! Windoze refused to enable UDMA on this drive no matter what i tried) and i've configured Ubuntu to apply the hdparm optimizations at every boot. 

I'm now starting to install more software that i need. 

So far so good.

---

