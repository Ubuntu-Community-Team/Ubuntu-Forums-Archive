---
title: "Nvidia 7600 woes"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by jackpetrilli on 2008-01-04
I've just recently upgraded from a Nvidia 5600 card to a 7600 GT one.  I cannot get Ubuntu 7.10 to recognize it.  I was using the restricted drivers.  I've researched and printed out 13 pages of notes which had me trying everything, from changing H/V frequencies in xorg.conf, to running ENVY, to running sudo dpkg-reconfigure xserver-xorg commands (and all their myriad variations).  NOTHING WORKS.  I get the same darn 800x600 at 85hz option only.

If anyone thinks they can help me, it would be much appreciated.

- Jack

---

### Post by bodhi.zazen on 2008-01-05
you need to :

1. remove the nvidia-glx package

2. install the nvidia driver (envy or manually)

3. if needed, run ```
gksu nvidia-settings
```

---

### Post by ryanVickers on 2008-01-05
Yeah, I would make sure you've just got the right driver - I have an nVidia 7600 GT and have had no problems at all since 7.04 (and now run 7.10 perfectly) - just click on the restricted driver and its done! :)

---

### Post by jackpetrilli on 2008-01-05
> **bodhi.zazen said:**
> you need to :

1. remove the nvidia-glx package
2. install the nvidia driver (envy or manually)
3. if needed, run ```
gksu nvidia-settings
```

Thanks for your attempted help but this didn't work.  I keep getting a startup message that says:

"Your screen and graphics card could not be detected correctly."

Then it drops down to 800x600 low graphics mode.  My card is an EVGA 7600 GT (Nvidia). I've been working on this for hours now (see my 1st thread) and I'm starting to think it's "unfixable."  Is there a repair mode in Ubuntu?  Am I forced to go back to Vista?  I've invested a lot of time in setting up my Ubuntu the way I want it, but I'm not willing to go back to my old graphics card.  I need some serious help here...

- Jack

---

### Post by overdrank on 2008-01-05
> **jackpetrilli said:**
> Thanks for your attempted help but this didn't work.  I keep getting a startup message that says:

"Your screen and graphics card could not be detected correctly."

Then it drops down to 800x600 low graphics mode.  My card is an EVGA 7600 GT (Nvidia). I've been working on this for hours now (see my 1st thread) and I'm starting to think it's "unfixable."  Is there a repair mode in Ubuntu?  Am I forced to go back to Vista?  I've invested a lot of time in setting up my Ubuntu the way I want it, but I'm not willing to go back to my old graphics card.  I need some serious help here...

- Jack

Hi once you installed the new drivers you may need to reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by SOULRiDER on 2008-01-05
Make sure you installed the packahe **nvidia-glx-new** and **NOT** just **nvidia-glx**

---

### Post by jackpetrilli on 2008-01-06
> **overdrank said:**
> Hi once you installed the new drivers you may need to reconfigure your xorg
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Okay... didn't work... but here's the strange thing.  I can get my high resolution if I choose VESA when I'm executing the above command.  But I drop down to low res mode if I try to pick NVIDIA as my driver.  For some reason, ubuntu isn't reading my graphics card (though both Vista and XP had no problem with it).

Once again the card is an EVGA 7600 GT (Nvidia).

I'm pretty sure that the problem is that Ubuntu can't read my card, hence trying to use the Nvidia driver confuses the system ("What Nvidia?  You don't have a Nvidia!" - ubuntu) and that's why it drops into low res graphics.

Does anyone have any ideas on how I can force Ubuntu to properly read my card?

- Jack

---

### Post by overdrank on 2008-01-06
> **jackpetrilli said:**
> Okay... didn't work... but here's the strange thing.  I can get my high resolution if I choose VESA when I'm executing the above command.  But I drop down to low res mode if I try to pick NVIDIA as my driver.  For some reason, ubuntu isn't reading my graphics card (though both Vista and XP had no problem with it).

Once again the card is an EVGA 7600 GT (Nvidia).

I'm pretty sure that the problem is that Ubuntu can't read my card, hence trying to use the Nvidia driver confuses the system ("What Nvidia?  You don't have a Nvidia!" - ubuntu) and that's why it drops into low res graphics.

Does anyone have any ideas on how I can force Ubuntu to properly read my card?

- Jack

HI and have you tried what was posted previously about removing the nvidia-glx package in synaptic manager? You will need the nvidia-glx-new. Have you tried Envy?

---

### Post by Peter09 on 2008-01-06
Sorry to sort of hijack the thread, but has someone actuall got an Nvidia 7600 working? I have tried everything and endup with a black screen with the terminal saying 'no input detected'. Any pointers to useful threads?

---

### Post by SOULRiDER on 2008-01-06
My friend has that card i believe and ig ot ti working at his house the toher day but it didnt work out of the box for some reason.

Heres what i'd do.
```
sudo aptitude remove nvidia-glx
sudo aptiude install nvidia-glx-new
```
Edit ```
/etc/X11/xorg.conf
```
to use the nvidia driver instead of nv.

Restart X with
```
ctrl + alt + backspace
```
If the resolution is still bad try to change it from the menu (in System > Preferences > Screen Resolution).

If that doesnt work try:
```
sudo dpkg-reconfigure xserver-xorg
``` selecting the nvidia driver, not nv or vesa.
Reboot and if the res is still bad try to change it from System > Preferences > Screen Resolution.

---

### Post by drs305 on 2008-01-06
> **Peter09 said:**
> Sorry to sort of hijack the thread, but has someone actuall got an Nvidia 7600 working? I have tried everything and endup with a black screen with the terminal saying 'no input detected'. Any pointers to useful threads?

I use the Nvidia GeForce 7600 GS without any issues. I have System, Admin, Restricted Drivers, Nvidia accelerated graphics driver checked. In synaptic, I have nvidia-glx-new and nvidia-kernel-common installed.

Gutsy 64-bit

---

### Post by aktiwers on 2008-01-06
You could always try install them manually. I always get best results that way. I posted howto here:
[http://ubuntuforums.org/showthread.php?t=657713](http://ubuntuforums.org/showthread.php?t=657713)

In post number 7

---

### Post by jackpetrilli on 2008-01-06
> **overdrank said:**
> HI and have you tried what was posted previously about removing the nvidia-glx package in synaptic manager? You will need the nvidia-glx-new. Have you tried Envy?

Yes to both questions.  No luck.

- Jack

---

### Post by jackpetrilli on 2008-01-06
I tried installing the latest Nvidia drivers as per a previous post in this thread.  It installed but still no luck.  I still maintain that my problem is Ubuntu cannot properly find my 7600 card.  When I look in my xorg.conf file, the driver is reported as Nvidia BUT THE VIDEO CARD IS REPORTED AS "GENERIC VIDEO CARD."

Does anyone have any idea on how I can get Ubuntu to properly recognize the card?

- Jack

---

### Post by jackpetrilli on 2008-01-06
> **jackpetrilli said:**
> When I look in my xorg.conf file, the driver is reported as Nvidia BUT THE VIDEO CARD IS REPORTED AS "GENERIC VIDEO CARD."

Does anyone have any idea on how I can get Ubuntu to properly recognize the card?

- Jack

Just to add to the above... What would stop Ubuntu from properly recognizing the card (An EVGA 7600 GT)?  

(As stated before, the card was recognized and set up in Vista and XP, so there's nothing wrong with the card.  Vista's device manager recognizes the card as a "NVIDIA GeForce 7600 GT," with Driver Version 7.15.11.5818 provided by Nvidia, dated 12/04/2007).

Anyone?

- Jack

---

### Post by bodhi.zazen on 2008-01-06
See if this link helps : [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-35311afc21ce57e599c941cd303233d2f0b3be23](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-35311afc21ce57e599c941cd303233d2f0b3be23)

---

### Post by Watchguy on 2008-01-07
I have a XFX 7600 GT Fatality 1. It was recognized by 7.10 64 bit on first installation and worked fine. I did go to the XFX site and update the drivers but not because it wasn't working, I just wanted the latest drivers.

---

### Post by ryanVickers on 2008-01-07
yeah, like I said al ong time ago, I have the EVGA nVidia GeForce 7600GT and its never been a problem... (after they invented the restricted drivers manager that is ;))

---

### Post by jackpetrilli on 2008-01-07
> **bodhi.zazen said:**
> See if this link helps : [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-35311afc21ce57e599c941cd303233d2f0b3be23](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-35311afc21ce57e599c941cd303233d2f0b3be23)

Nope.  No go.  xorg.conf still says Nvidia driver BUT generic card.

- Jack

---

### Post by jackpetrilli on 2008-01-08
> **ryanVickers said:**
> yeah, like I said al ong time ago, I have the EVGA nVidia GeForce 7600GT and its never been a problem... (after they invented the restricted drivers manager that is ;))

Would you be so kind as to send me your xorg.conf file?  (jack5746@gmail.com)  Or post it here if you prefer.  

(If ANYONE has the 7600 GT card and it's working in Ubuntu, please post your xorg.conf!!!)

- Jack

---

### Post by jackpetrilli on 2008-01-08
Okay, I just reinstalled Ubuntu 7.10.

My problem is simple... the nvidia proprietary drivers are simply not compatible with the 7600 GT card.  (Please bear in mind that the GT card is not quite the same as the GS one).

Ubuntu booted up in high res.  When I tried to use the proprietary drivers, it went back down to low res, with the same old "card not found" message, I've seen at least a thousand times now.)

Thanks to all of you who tried to help...

- Jack

---

### Post by radi0j0hn on 2008-01-08
I'm probably newer at this than you, but when I switched monitors, setting up the screen via the command line seemed to do the trick.

Off topic:   I still do not see why there are TWO resolution setting, one in preferences and one in administration.  I had trouble getting them  to agree and for the changes made to "stick."  John

---

### Post by ryanVickers on 2008-01-08
> **jackpetrilli said:**
> Would you be so kind as to send me your xorg.conf file?  (jack5746@gmail.com)  Or post it here if you prefer.  

(If ANYONE has the 7600 GT card and it's working in Ubuntu, please post your xorg.conf!!!)

- Jack

most certainly! ;)

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver        "nvidia"
    Busid        "PCI:5:0:0"
    Option        "AddARGBVisuals"    "True"
    Option        "AddARGBGLXVisuals"    "True"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    Horizsync    28-64
    Vertrefresh    43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Modes        "1280x1024"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
    
    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
EndSection
```now, mine might not be exactly the same as what it should be on your computer, but if you run the X reconfigure commend, it may work... or it may just work like this! :p

There were 2 more files called xorg.conf.# (3 = 1 or 2) and I've attached them just in case you need them or parts of them too

---

### Post by jackpetrilli on 2008-01-08
> **ryanVickers said:**
> most certainly! ;)


Thanks a lot Ryan... but it didn't work.  

Okay, so now I've given up on the nVidia proprietary drivers.  Right now the VESA driver is giving me 1280x1024 and my 2nd monitor is mirroring my main one.  Does anyone know if I'll be able to set up a dual monitor system (ie one big desktop across both monitors) using Xinerama with the VESA driver?

This would be an acceptable compromise for me...

- Jack

---

### Post by bodhi.zazen on 2008-01-09
> **jackpetrilli said:**
> Thanks a lot Ryan... but it didn't work.  

Okay, so now I've given up on the nVidia proprietary drivers.  Right now the VESA driver is giving me 1280x1024 and my 2nd monitor is mirroring my main one.  Does anyone know if I'll be able to set up a dual monitor system (ie one big desktop across both monitors) using Xinerama with the VESA driver?

This would be an acceptable compromise for me...

- Jack

Ah, no joy with the vesa driver. Nvidia or bust that way.

---

### Post by jackpetrilli on 2008-01-14
I solved my problem with Ubuntu and the nvidia 7600 card!  And I solved it through pure fluke.. and by installing Mandriva!

I was trying to find a Linux distro that would work with my card.  I finally settled on Mandriva.  Imagine my surprise when Mandriva also wouldn't accept my 7600.  But it gave a REASON why it wouldn't take the card.  Not enough power.  It even told me how to fix the problem - by attaching a supplementary power cable to my power supply.  Not having changed a graphics card in a couple of years, I didn't even REALIZE that these cards now need extra power from the power supply.  Off went my computer case; on went the cable.  Voila - Mandriva now worked.

Well, if Mandriva now worked with this hardware fix, why not Ubuntu?!  Off went Mandriva; on went Ubuntu.  Everything works perfectly now with my 2 monitors controlled by TwinView.  I didn't even have to TOUCH xorg.conf - twinview did it for me.

Damn!  After a week of pure grief, it took me less than 5 minutes to install that damn power cable.  Well, at least it's solved now...  (And thanks again to all those who tried to help.)

- Jack

---

### Post by ryanVickers on 2008-01-14
> **jackpetrilli said:**
> I solved my problem with Ubuntu and the nvidia 7600 card!  And I solved it through pure fluke.. and by installing Mandriva!

I was trying to find a Linux distro that would work with my card.  I finally settled on Mandriva.  Imagine my surprise when Mandriva also wouldn't accept my 7600.  But it gave a REASON why it wouldn't take the card.  Not enough power.  It even told me how to fix the problem - by attaching a supplementary power cable to my power supply.  Not having changed a graphics card in a couple of years, I didn't even REALIZE that these cards now need extra power from the power supply.  Off went my computer case; on went the cable.  Voila - Mandriva now worked.

Well, if Mandriva now worked with this hardware fix, why not Ubuntu?!  Off went Mandriva; on went Ubuntu.  Everything works perfectly now with my 2 monitors controlled by TwinView.  I didn't even have to TOUCH xorg.conf - twinview did it for me.

Damn!  After a week of pure grief, it took me less than 5 minutes to install that damn power cable.  Well, at least it's solved now...  (And thanks again to all those who tried to help.)

- Jack

Wow nice! :D

My 7600 GT doesn't need anything else though, and I have it over clocked by 200Mhz :rolleyes: (and technically it came like that so I'm also off the hook if something goes wrong :D)


Anyways, back to the point, glad you solved it, interesting though that mine does not need or even haev an extra power plug in.  it's PCI express, right?

I wanted to just try out one of the 8800's so I "rented" one from the store and it had an extra power plug, so of course I had to use one then, but not my 7600, its doesn't have one...

so I'm just wondering... :confused:

---

### Post by jackpetrilli on 2008-01-14
> **ryanVickers said:**
> Wow nice! :D

My 7600 GT doesn't need anything else though, and I have it over clocked by 200Mhz :rolleyes: (and technically it came like that so I'm also off the hook if something goes wrong :D)


Anyways, back to the point, glad you solved it, interesting though that mine does not need or even haev an extra power plug in.  it's PCI express, right?

I wanted to just try out one of the 8800's so I "rented" one from the store and it had an extra power plug, so of course I had to use one then, but not my 7600, its doesn't have one...

so I'm just wondering... :confused:

My motherboard is an older Asus p4p800 which needed an AGP graphics card - no PCI express and I guess that's why it needed the extra power.  Vista worked well without the extra cable and so did XP - though XP did give me a msg that the card was underpowered.

Mystery solved...

- Jack

---

### Post by ryanVickers on 2008-01-14
ok, because my 2 main boards are a Gigabyte nForce 4 Pro SLI and the more commonly known ASUS A8V-E SE...

If your wondering why I have "2 main boards"... don't ask, long story... ](*,)

---

