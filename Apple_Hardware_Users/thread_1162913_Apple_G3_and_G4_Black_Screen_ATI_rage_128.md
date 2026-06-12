---
title: "Apple G3 and G4 Black Screen ATI rage 128"
date: 2009-05-18
forum: Apple Hardware Users
---

### Post by AndyMarsh on 2009-05-18
Okay, first post. I would be a new user to Linux if I could get the thing working! Arghhh!!!!

Really want to get using Linux on my Mac but can't get past the Black Screen of Death…

Machines:
Apple G3 Blue and White 350Mhz 6Gb 256Mb ATI Rage 128 PCI
Apple G4 400Mhz 6Gb 256Mb ATI Rage 128 AGP

Distributions:
Ubuntu 8.10 CD ISO install
Debian
Xubuntu 7.10 <---- This one works fine but is limited by not allowing me to download software such as Scribus

Problem:
Installed Ubuntu 8.10 on BOTH machines and have SAME problem.
Installer works well, Apart for the (no CD-ROM bug) at the beginning
Once installed the screen goes black and hard disk activity stops.
Press CTRL + F1 and type sudo nano /etc/X11/xorg.conf and magicallly this file is EMPTY
Try to add info about monitor and refresh rates (HorizSync 30-83) (VertRefresh 56-75) according to my monitor these are correct. 

Still blank screen on startup. I have been at this for two days straight. I have ordered CD distros of Fedora and Debian but I fear that once they arrive I will have the same problem.

Is the ATI rage 128 card supported at all in ubuntu?
Is there a driver that I need to download from a repository or something alse that I am missing.

Surely this is not an isolated issue as I have tried this on two machines and a friend has had the EXACT same problem on his Apple G4 400mhz.

I can login to the low res video=ofonly nosplash place but none of the apps work on the G3 and the mouse does not work on the G4.

Any ideas guys?

---

### Post by Benboom on 2009-05-18
I don't know what the answer to your problem is but I do have two G4s here (AGP Sawtooth towers - a 450 and a 400 with a 1g accelerator) and they both run 9.04 fine. I haven't installed it on the machine with the accelerator but it runs very well under the Live CD. The 400 runs it fine as an installation and most everything works (thanks to the helpful people here); however, I never had the problem you describe during the installation process.

My system profiler shows Chipset ATY, Rage128Pro. [Yes, it says ATY, not ATI]

So I don't know why it wouldn't work on your system, too.

---

### Post by AndyMarsh on 2009-05-18
Thanks for your reply Benboom. So basically you cannot use Ubuntu 8.10 on a G4 or G3 with a Rage 128 card. It is very strange because Xubuntu installs and works perfectly. The hardware is working correctly as I am able to install Ubuntu and Debian. It's just the display hardware that is stopping the GUI from working.

---

### Post by stream303 on 2009-05-18
> **AndyMarsh said:**
> Okay, first post. I would be a new user to Linux if I could get the thing working! Arghhh!!!!

Don't base your judgement about Linux on how it is supported for Apple PPC boxes, which are notoriously fickle for a beginner due to the large amount of Apple-specific quirks that Linux installers have no way of handling automatically.

> Machines:
Apple G3 Blue and White 350Mhz 6Gb 256Mb ATI Rage 128 PCI
Apple G4 400Mhz 6Gb 256Mb ATI Rage 128 AGP

Concentrate on getting the G4 to work first.  That would represent the very minimum to me for usability, as G3's are really just a technical exercise in frustration, unless you know how poorly they are going to perform up front. :)

When all is said and done, you'll have the equivalent on the G4 to about an 800mhz Intel box with 256mb of ram.  It's not going to be zippy, and you won't have full flash support as there is only a work-in-progress with gnash.

> Distributions:
Ubuntu 8.10 CD ISO install
Debian
Xubuntu 7.10

By all means try the latest Jaunty 9.04. Earlier versions had a number of mind-numbing bugs. I recommend the "alternate" text-based installer:

[http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

> Press CTRL + F1 and type sudo nano /etc/X11/xorg.conf and magicallly this file is EMPTY. Try to add info about monitor and refresh rates (HorizSync 30-83) (VertRefresh 56-75) according to my monitor these are correct.

That's correct.  But you know how to do it manually, armed with the correct frequencies for your monitor.

To help out, here's a more populated version that can serve as a template for editing and additions, even though it is still a bit empty. :

**NOTE that the BusID you see here is for MY iMac, and you may not need this line at all for yours.**

```
Section "Device"
        Identifier      "Configured Video Device"
        BusID           "PCI:240:16:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       xx-xx
        VertRefresh     xx-xx
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        DefaultDepth    24
            SubSection "Display"
              Depth        24
              Modes      "1024x768"
            EndSubSection
EndSection
```

Use the native-resolution of your monitor instead of "1024x768" if it is different.

> Still blank screen on startup. I have been at this for two days straight. I have ordered CD distros of Fedora and Debian but I fear that once they arrive I will have the same problem.

That is correct.  Fortunately what you learn here is also directly applicable to Debian, and even to Fedora for the most part.

> Is there a driver that I need to download from a repository or something alse that I am missing.

You should have a much easier time with Jaunty 9.04, since the ati drivers have been replaced with more generic ones, so you may not have to fiddle with driver settings at all - just concentrate on getting your vertical/horizontal frequencies correct for your external monitor, and perhaps a setting in xorg.conf like:

```
Modes "1024x768"
```

To force the proper video resolution to whatever is the native resolution of your monitor.

> Surely this is not an isolated issue as I have tried this on two machines and a friend has had the EXACT same problem on his Apple G4 400mhz.

Exactly - with many Apple boxes, one has to nearly always manually modify /etc/X11/xorg.conf themselves.  You may get lucky with more modern G4 and G5's but don't count on it. :)

> I can login to the low res video=ofonly nosplash place but none of the apps work on the G3 and the mouse does not work on the G4.

Two outstanding kernel parameters - especially nosplash, which seems to haunt Ubuntu until the end of time.  If those work, you can make those kernel parameters permanent by editing the "append=" lines in /etc/yaboot.conf, and then performing *sudo ybin -v* to make the system aware of the change.

---

### Post by AndyMarsh on 2009-05-18
Cheers Stream303.

The main reason for me installing on these machines is to learn Linux but also to see how well it performs. I will seek out a version of Jaunty that I can get on CD as I am on mobile broadband with 3 here in Sydney and they charge AU$100 per GB! Will report back my progress with Jaunty whenthe disks arrive.

I have a feeling that tjis Linux adventure is JUST beginning for me! :)

Andy.

---

### Post by Benboom on 2009-05-18
Both of my G4s boot up fine in Jaunty without an edited xorg.conf file, but they only showed two resolutions (800x600 and 640x480) before editing. However, I never got a black screen so I assume the difference is that I was using 9.04 and you are trying to use 8.x.

---

### Post by AndyMarsh on 2009-05-18
Hi Benboom

I reckon the only way for me to find out if it is an 8.x problem is to get 9.04 and install it! :) guess I should go searching eBay to see if I can get the disk.

Andy.

---

### Post by stream303 on 2009-05-19
> **Benboom said:**
> Both of my G4s boot up fine in Jaunty without an edited xorg.conf file, but they only showed two resolutions (800x600 and 640x480) before editing. However, I never got a black screen so I assume the difference is that I was using 9.04 and you are trying to use 8.x.

Some machines don't immediately barf on the splash screen - you either sit in total blackness for awhile, or are greeted by some 1970's acid-graphics temporarily until you get to X.  However, some models just totally lock up on the splash screen and get no further requring the "nosplash" parameter at boot time (then later permanently added to /etc/yaboot.conf followed with a *sudo ybin -v* to make it stick.

The good news with the lower-resolution graphics is that it just means you have to convince the Apple hardware to use the resolution it is actually capable of - but you have to manually tell it to do so by editing /etc/X11/xorg.conf yourself.  To get these resolutions, you may also have to specify the vertical and horizontal frequencies in xorg.conf too.

Low-graphics means that one is almost home-free.

---

### Post by AndyMarsh on 2009-05-19
Hey Benboom,

I FINALLY got it to work. Three days perseverance really paid off! It was the xorg.conf file. I had to reduce the HorizSync down so that the monitor could display the signal! Thak you guys for your responses. What a great intorduction to the open source community.:p

Andy.

---

### Post by stream303 on 2009-05-21
Glad it's working!

Copy or print out that xorg.conf file for reference!  (off the machine!).  You might need it later on.  I've spent months tweaking an xorg.conf only to have the machine crash and not have any notes when I had to start all over again. :)

Also copy or print out your /etc/yaboot.conf

---

### Post by 10011010 on 2009-05-23
Xorg can definitely be one of the hardest pieces to new linux users.

---

