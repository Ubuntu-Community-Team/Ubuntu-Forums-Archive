---
title: "higher resolution isn't available"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Irishpolyglot on 2007-05-26
Hi everyone!! I'm still ironing out a few problems before I can really transfer myself over to Ubuntu. It's installed and I'm trying to get the wireless working (other thread), but what's quite annoying is the resolution is stuck at 1024x768. I've gone into the settings and the only other options are all less than this. I have a DELL Inspiron 9400 with a WideScreen 17" WXGA+ (1440x900) LCD Ultrasharp TFT Display and Nvidia 256MB GeForce Go 7900 GS PCI Expressx16 Graphics Card. Do I need nvidia drivers? What should I type into the terminal to do this?
Thanks!!

---

### Post by Simran on 2007-05-26
Hi :)

For a higher widescreen resolution i use: 

sudo apt-get install 915resolution

Once installed just do: 

sudo 915resolution mode Xresolution Yresolution so 
sudo 915resolution mode 1440 900

job done :) then it keeps it as your default.

As for drivers, if your using 7.04 fiesty System > Administration > Restricted Drivers Manager 
It should auto-detect them and you just enable them.

Simran

---

### Post by H.E. Pennypacker on 2007-05-26
Simran, if I am not mistaken 915resolution is for Intel graphics cards.

For your resolution problems, please see:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Also, because resolution problems are quite common, please do a forum search.  Make sure you also install necessary NVIDIA drivers.  I believe something called Envy can help you do this (install those drivers).

---

### Post by Simran on 2007-05-26
> **H.E. Pennypacker said:**
> Simran, if I am not mistaken 915resolution is for Intel graphics cards.


You aren't, my bad:---)

Simran

---

### Post by joelcont on 2007-05-26
**[COLOR="DarkOrange"]i got the same problem ......[/COLOR]**

---

### Post by Ek0nomik on 2007-05-26
Install your video card drivers.

System/Administration/Restricted Drivers

Restart and you should see your new video resolution options.

If not, you can edit your xorg.conf file to give you those resolutions, or you can run a configure command.

```
sudo gedit /etc/X11/xorg.conf
```

SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection

You will see something like that.  Just add resolutions.  You can see I manually added 1680x1050 to my xorg so I have that option.

You can probably also run:

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Irishpolyglot on 2007-05-26
Thanks again Pennypacker!! Envy did the trick ;-)

---

### Post by maduranga on 2007-09-04
:)

---

### Post by n3tfury on 2007-09-04
> **Simran said:**
> You aren't, my bad:---)

Simran

you should edit out your first post or remove it altogether before someone uses it later who's got the same hardware as the OP.

---

