---
title: "Ubuntu 8.04 stuck at 800+600 on my PowePc G4 dual! Help?"
date: 2009-03-01
forum: Apple Hardware Users
---

### Post by sastusbulbas on 2009-03-01
Hello,

I have managed to get Handy Heron 8.04 to run on my Apple PowerMac G4 Dual AGP.

But my screen resolution is stuck at 800 + 600.

Can anyone give me a step by step guide to doing something to rectify this?

I am a complete novice so easy to understand please.

Steve

---

### Post by ForMar on 2009-03-01
I'm not trying to be mean and I hate to sound like one of those customer services guys who ask if your computer is plugged in but, did you try changing it by clicking system on the top bar -> preferences -> Screen Resolution (it should be fifth from the bottom.

---

### Post by sastusbulbas on 2009-03-01
Yes,

It only has that single option, it's an old G4 Dual cpu with teh ATI rage 128 AGP 4X graphics. Ubuntu seems to be running fine but no graphics option.

I have installed Ubuntu onto a PC in the past but it was very straight forward, though it was when Ubuntu was not long out, and I cannot remember much about it. I still have it on a Hard drive somewhere, got as far as Aero desktops and such.

I have two drives for this, one for Ubuntu and the other for OS 10.1.5

The system original OS (10.1.5)can be used with a resolution of 1680+1050 but can only be used with Internet Explorer 5, pretty poor and the OS is very limited.

---

### Post by sastusbulbas on 2009-03-08
Bumpy poos?

Anyone? Or is it true that Ubuntu is really only for intel based stuff these days? :(

---

### Post by hictio on 2009-03-08
What monitor are you using? Do you have the tech specs of it? Specially the vertical and horizontal refresh rates? If not Google for those.

Once you have them, you' ll need to edit the file '/etc/X11/corg.conf' via sudo, to add those values.

The '/etc/X11/corg.conf' had to end something like this (use the values for your monitor!!!):

```

Section "Monitor"
        Identifier      "Samsung SyncMaster 920NW"
        VendorName      "Samsung"
        Modelname       "920NW"
        Horizsync       30-81
        Vertrefresh     56-75
EndSection

```

And also, its very likely that you'll have to add the desired resolution to the another section of the configuration file as well (use your resolutions!!!):

```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung SyncMaster 920NW"
        Device          "NV11 [GeForce2 MX/MX 400]"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"

        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x1024" "1280x960" "1024x768" "800x600"
                Viewport        0 0
        EndSubSection
EndSection

```

First of, I would say that you should get the refresh rates, then make a copy the current xorg.conf file, and then edit it.

To make a copy of the current config file, type this on a Terminal:

```

sudo cp /etc/X11/corg.conf /etc/X11/corg.conf.working.copy ENTER

```

It will ask your password after the ENTER, type it, and then ENTER again.

To edit the file, if you are using Gnome, type this on a Terminal:

```

sudo gedit /etc/X11/corg.conf ENTER

```

If you execute this right after making the copy, it will not ask your password once again.
When you are done editing it, save it. and either reboot the box, or type Ctrl + Alt + Backspace to force a re-init of the graphical environment.

---

### Post by oswaldkelso on 2010-04-23
I use this method

HOWTO: Choose the resolution YOU want in xorg.conf

[http://forums.debian.net/viewtopic.php?f=16&t=26577](http://forums.debian.net/viewtopic.php?f=16&t=26577)

---

### Post by sastusbulbas on 2010-05-01
Still not sorted this, not sure what I open to copy/paste what where. 

What I did do was stick a new PCI Mac edition ATI 9200 graphics card in, no problems choosing 1600+1050 with that installed. This not not a decent solution though, the card is worth more than the PPC on the second hand market.

Why has this issue not been solved with the 9.10 release? As I had this issue back when 8.04 was first released and it looks like others did too?

Original problem posted 1st of March 09 over a year ago, currently 1st of May 2010 with the same resolution issues on 8.04 and 9.10 when running a PPC's original AGP card.

---

### Post by linuxopjemac on 2010-05-02
These old ATI/nVIDIA cards are difficult to configure. The newer graphic cards are found and configured automatically. For the old ones you need to make your own xorg.conf file, which is difficult. What are the specs of your machine and monitor?

---

