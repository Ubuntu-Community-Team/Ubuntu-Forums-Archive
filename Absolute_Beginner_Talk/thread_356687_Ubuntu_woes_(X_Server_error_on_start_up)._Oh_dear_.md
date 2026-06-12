---
title: "Ubuntu woes (X Server error on start up?). Oh dear :("
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Dave1271 on 2007-02-08
First off, apologies if this is in the wrong area. I saw "Absolute Beginner Talk" and fled straight here.

Next up, system specs.

I currently use:
**Motherboard: ** ASUS K8V-VM
**Grapics Card: ** Radeon x1950 Pro
**RAM: ** 2GB DDR400
**CPU: ** AMD64 3800+ (ClawHammer)

Everything else used, such as LAN, is onboard.

**Ubuntu Version I'm using is 5.10**

**Background:** (A.k.a My Boring Day.)
I recently got my sparkly new graphics card (the x1950 pro) into my PC and was loving it on my Windows XP. However, Windows decided that it did not like my enjoyment and wanted to stop booting up. After much fussing and fiddling around, I decided to simply reinstall Windows. After much more fussing and fiddling around, I decided I had no idea where my Windows XP CD was, so that was out of the question. And then I spotted my Ubuntu disk which my friend gave to me a while back, shrouded in a halo of light - as if sent by the heavens themselves!

**Main problem:**
So, I installed Ubuntu, following the installation steps etc. until the setup was complete. After making my username etc. then booting the PC up, I get to the Ubuntu login screen. And then - before I can even log in - I get an error yapping about "X Window":

**"Failed to start X server (your graphical interface. It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the program?".**

Now, as I'm on my laptop at the moment I'll type out the output upon request. I don't fancy typing out all that, so I won't do unless asked.


Total guess: this is something to do with drivers or the like? If so, I have my driver disks for both the motherboard and graphics card, but I'm totally and 100% clueless as to how to go about installing them with the ubuntu command prompt thingy that comes up.



Any help is appreciated, and if I'm a bit off on the placement of the topic (IE: incorrect forum) then I apologise again. I saw a "help and support" area but it was quite daunting with its 10 sub-forums :-( So I stuck to something that sounded familiar - "absolute beginner".

Thanks,
Dave.

---

### Post by daou on 2007-02-08
The version you used is a bit old. It probably doesn't have all the needed modules handle your hardware. It looks quite new.

If possible, I suggest you get Ubuntu Edgy 6.10 and install it instead.

---

### Post by Dave1271 on 2007-02-08
'Kay, will do! 

Thanks for the fast response, and the advice!

---

### Post by daou on 2007-02-08
If you still want to give the 5.10 a shot, [this page will help]("http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide"). Your ATI gfx card is probably the problem.

I still suggest 6.10 though. You might not be able to get 5.10 working with such a new gfx card. The help page for 6.10 is here[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").

---

### Post by Dave1271 on 2007-02-08
The 6.10 download is currently on 45% and going strong at 1,200kb/s so I think I'll just install that :)

I'm not attached to 5.10 or anything - it's just what I had at hand :P


Thanks again

---

### Post by Maestro23 on 2007-02-08
> **Dave1271 said:**
> The 6.10 download is currently on 45% and going strong at 1,200kb/s so I think I'll just install that :)

I'm not attached to 5.10 or anything - it's just what I had at hand :P


Thanks again

This guide will help with your ATI card: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Dave1271 on 2007-02-09
Hi again,

I downloaded the 6.10 Edgy version and burned the image to CD, but when I attempt to install Ubuntu I get to a "Ubuntu" loading screen, where I can see the logo and a sliding loading bar... and then it freezes. The loading bar stops moving, and I left it for 45 minutes to see if it would come back, but it didn't...

This happens every time :S

Is this a problem with my hardware? I had a "Kernel Panic" error once when installing 5.10 and had to restart, but other than that it was clean and easy.

Thanks again for your help and support,
Dave

**EDIT:** Eek. Now I'm getting the following error upon start up:
> [1717957.696000] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0
[17179572.320000] Kernel panic - not syncing : VFS : Unable to mount root fs on unknown-block (1,0)
[17179572.320000] 

Oh dear again :(

By the way, my hard drive is a 120GB Samsung IDE hard drive, if that matters to anyone.

---

### Post by Zuuswa on 2007-02-09
try editing your xorg.conf file manually:
```
sudo nano /etc/X11/xorg.conf
```

and look for something like this:
```
Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "ati"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection
```

That is my xorg.conf section, so it will not look exactly the same.  Try changing the dirver line to "ati" or "radeon", and then hit control+x to save your document.  Then try starting your X server either by typing startx in the console or by rebooting.

as for this error:
>  [1717957.696000] PCI: Cannot allocate resource region 8 of bridge 0000:00:03.0

it is not a problem . . . I get several of them whenever I boot and it has no impact on any functionality

---

### Post by -Ghost9- on 2007-02-09
I had the exact same issue you are having. except for the panic thing.
You have to install with an alternate CD so that you can install in text mode.

After installing in text mode it will still freeze if you start it up normally, so instead start it up in recovery mode. Once you get to the command prompt, follow these instructions(they worked for me):

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

That should get you into the graphical interface. Myself I had to do these instructions below also to get 3d rendering working after I got the windows side working.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

---

### Post by houstonbofh on 2007-02-09
You do need to know that all of these fixes require things from the repository that are broken right now. [http://www.ubuntuforums.org/showthread.php?t=35640](http://www.ubuntuforums.org/showthread.php?t=35640) Understand that when you have this issue, it ain't you. :)

---

### Post by Dave1271 on 2007-02-09
Thanks for all the replies guys - but I gotta go out for now. I'll give the stuff suggested a try once I get back :)

Will let you know how it goes ;)

---

