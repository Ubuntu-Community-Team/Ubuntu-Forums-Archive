---
title: "Xbuntu &amp; XFCE"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by holmer.green on 2006-11-15
I am testing xbuntu dapper as a "light" OS to replace WIN98 on 20 school PCs. They are all under 1GHz and on average 128 mb. On a test PC I have installed two HDDs. First I installed Win98 to C drive (master). Then installed xbunto server install on second HDD. Everything works from grub menu. My problem is that I want to keep install "light". Was intending to use XFCE desktop. As my research indicated this was best route. At command line typed "sudo aptitude install x-window-system-core xfce4". This completed. Rebooted (number of times) but would not recognise startxfce4. Did "whereis xfce4" but not found. Looking on forum found post that said you should also "sudo apt-get install xubunu-desktop". It said I would be given the xfce option in sessions. The install is still running. I will come back and post result but my questions are (1) not sure what "xfce option in sessions" means. (2) Does what I have done defeat my objective of keeping a light install and can anyone give me better guidance?

---

### Post by Peter76 on 2006-11-15
Hello, "xfce option in sessions" means xfce will show up in the gdm menu ( this is a graphic way to login to your system ). 
As for your second question, it depends the hardware a bit... Xubuntu is fairly lightweight, but if it is still to sluggish for you, look at my icewm howto here:

[http://www.ubuntuforums.org/showthread.php?t=171203](http://www.ubuntuforums.org/showthread.php?t=171203)

Or search the forums for fluxbox, wich is another lightweight window manager. I'm running my icewm configuration at a pentium 11 at 400 mhz with 128 ram and it runs excellent.
You might want to replace rox-filer with thunar though, because that is a bit more intuitive, but you'll probably have to look around the thunar manual a bit to have it work your way ( I don't have a lot of experience with it )

Good luck, Peter

---

### Post by dbatchelor on 2006-11-15
I managed to install XUBUNTU from the ISO image xubuntu-6.10-alternate-i386.iso (I had problems with a variety of Debian distributions Skole LInux, Edubuntu- PC 400MHz and 128Mb RAM ).  It is I think fast enough for the children and although the desktop has some bugs (changing languages) its o.k.

---

### Post by holmer.green on 2006-11-15
Thank you for your very fast reponses. Completed the "install xubuntu-desktop". Rebooted could then see the unbuntu logo and the commands as they were being processed. Then screen flickered and went black. Could hear the HDD processing so must assume that the video driver is not supported. This is the most elderly of the PCs. Using this one as the test thinking if I could get this going the others would work. To set the scene I am a very experienced IT engineer but only with Microsoft. This is my first real install of a distro. There is a huge financial pressure on the school I support so am determined to prove to the Head that we can upgrade on the back of xbuntu.

---

### Post by dwblas on 2006-11-15
> Completed the "install xubuntu-desktopI am assuming that the install cd was able to recognize the video card, which means it should be ok.  Does "the screen goes black after the Ubuntu logo" mean before or after you see the grub screen and it starts to boot.  If before, then it is a grub problem.  If after, it may well be your video card, but it should take you back to the command line where you can then configure a generic interface that should work on just about any card.

---

### Post by holmer.green on 2006-11-15
Boots up to grub. Select xbuntu. Starts loading (all can be seen) with unbunto logo at top with graphical progress slide bar. Underneath all commands are shown being processed. Then screen goes black with flickering. Then goes solid black with white cursor at top left. Then cursor vanishes leaving black screen. All the time you can hear HDD processing data. Then silence!

---

### Post by kerry_s on 2006-11-15
I think you boned it, try reinstalling the full xubuntu from the start, instead of a server install. A server install is just good for a custom setup, i recommend you learn a little linux before trying a custom build. Xubuntu has most things you could use in a school from the get go and is alot easier than starting from scratch, when you don't know what apps do what or which ones to get.

I also recommend you grab a copy of DSL linux, just in case some of the machines are to old.-> [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by holmer.green on 2006-11-15
Kerry - Thanks for the input. I was thinking the same myself. If I screw up in windows I always know its quicker to start again. Lesson learned for linux. I am assuming that if I go for the full install I can remove applications I don't need. I am off to my workshop to start again! I will post my result!

---

### Post by dwblas on 2006-11-15
Agreed on installing the xubuntu iso.  I've installed xubuntu on machines from a 500 MHz on up and have never had a problem.  Get it going first and then look at networking.  As for the black screen, that could be many things.  When the window manager isn't configured properly, xorg will  somethimes boot twm, which is a really basic window manager.  I seem to remember that you just get an empty screen because it doesn't have anything else in it.  If you click all of the mouse buttons you will see some sort of menu, if you are in twm, but that is wasted time.  Just install the XUbuntu iso.  Note: I think XUbuntu comes with open office which is too much of a hog for what you have so just use Snyaptic to uninstall it.  You might also want to look at making some of the machines thin clients, but one step at a time.

---

### Post by K.Mandla on 2006-11-15
Actually, Xubuntu comes with Abiword and Gnumeric, which should be plenty light for those machines.

I've updated to Feisty from the Edgy Xubuntu install, and I see I also have OpenOffice.org Word Processor, but I'm not sure where that came from. ... :-k

---

### Post by holmer.green on 2006-11-15
Thanks. Install now running again. Will post tomorrow progress.

---

### Post by mo79 on 2006-11-15
Try IceWM perhaps? Install server and run:

```
sudo apt-get update
sudo apt-get install x-window-system-core xterm wdm icewm menu
```

You only need 1GB of space in total and requirements are perhaps equal/lower than XFCE. 
Installing the server first, as you've done, is an alright thing to try. It helps you understand quick that it's all like lego, you start with your base plate and work up. ;)

---

