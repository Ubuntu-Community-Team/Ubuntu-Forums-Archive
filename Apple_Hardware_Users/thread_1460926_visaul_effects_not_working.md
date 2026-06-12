---
title: "visaul effects not working"
date: 2010-04-23
forum: Apple Hardware Users
---

### Post by zeroti on 2010-04-23
No visual effects on ppc machine with new 10.04 install. (it was working on 9.10). When I select "normal" effects in the appearances control panel, a dialog pops up saying "searching for available drivers" and then, all of the open windows disappear and re-appear a couple of times and then a box pops up saying that "desktop effects could not be enabled".

i don't know how to find-out what version my graphics card is (please tell me how?) but i know it's ati.

is there a way to enable visual effects?

---

### Post by avtolle on 2010-04-23
> **zeroti said:**
> No visual effects on ppc machine with new 10.04 install. (it was working on 9.10). When I select "normal" effects in the appearances control panel, a dialog pops up saying "searching for available drivers" and then, all of the open windows disappear and re-appear a couple of times and then a box pops up saying that "desktop effects could not be enabled".

i don't know how to find-out what version my graphics card is (please tell me how?) but i know it's ati.

is there a way to enable visual effects?
To find out your graphics card, at the command line (Applications>Accessories>Terminal) do ```
lspci | grep -i vga
```
Good luck!

---

### Post by zeroti on 2010-04-23
This is my card:

0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by avtolle on 2010-04-23
[http://www.ubuntu.com/testing/lucid/beta1#Known%20issues](http://www.ubuntu.com/testing/lucid/beta1#Known%20issues) 

Take a look at this. I think this addresses your question (I don't have that card) and I think that you aren't going to have visual effects until the problem is resolved.

---

### Post by zeroti on 2010-04-23
Thanks. I looked at the bug report for the ATI issue and someone commented that AMD is ditching support for older graphics cards in their binary driver, so I'll have to wait until the open driver is optimized. I guess the older binary drivers aren't compatible with the new kernel.

Although, I don't remember seeing the binary driver listed in the Hardware Driver program before I updated to Lucid. Does that mean that I didn't have the binary one installed?

---

### Post by avtolle on 2010-04-23
Hazarding a guess, as I don't have that card: no, you did not.

---

### Post by zeroti on 2010-04-24
I was thinking: maybe I can get compiz to work if it was working before, so I took a look at this [PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz") and followed its advice.

This is my new /etc/X11/xorg.conf :

```

Section "Device"
    Identifier    "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
    Driver        "radeon"
    Option          "DynamicClocks" "true"
    Option          "AGPMode" "4"
    Option          "AGPFastWrite" "true"
    Option          "UseFBDev" "false"
    Option "DRI" "true"
    Option "GARTSize" "64"
    Option "AddARGBGLXVisuals" "true"
        Option          "XAANoOffscreenPixmaps"
        Option "DisableGLXRootClipping" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection

Section "ServerLayout"
    Option          "AIGLX"         "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```I get a better framerate for glxgears now. (about 450 in 5.0 sec)

I ran "compiz --replace" in the terminal and got this output:

```

compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :1.0

```That seems revealing. How do I disable software rendering?

EDIT: "glxinfo | grep render" produces:

```

direct rendering: Yes
OpenGL renderer string: Software Rasterizer

```

---

### Post by zeroti on 2010-04-24
Ok, so I've been looking at this article:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I updated my xorg.conf and I noticed that the Xorg.0.log shows:
```

(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2

```

It looks like DRI is being loaded, but it doesn't say that it's enabled,  like it is for glx:  "(==) AIGLX enabled"

This is my current xorg.conf:
```

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    BusID        "PCI:0:16:0"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

```

---

### Post by linuxopjemac on 2010-04-26
Maybe here you will get inspiration
[http://mac.linux.be/content/g4-emac-radeon-compiz](http://mac.linux.be/content/g4-emac-radeon-compiz)

---

### Post by zeroti on 2010-04-26
I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/570228](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/570228)

---

### Post by zeroti on 2010-04-29
**EDIT**: You can do the following but I've tried removing my xorg.conf after some of the updates to lucid and things went fine. So if you are fully updated, you prob. only need to disable KMS on your graphics card, but not create an xorg.conf if you don't have one.

Ok. I got it to work by disabling KMS on the radeon card and by using an xorg.conf.

But the question is: am I missing anything by not having the KMS for the radeon card?

In any case, here's what I put in /etc/modprobe.d/radeon-kms.conf :
```
options radeon modeset=0

```Here's my /etc/X11/xorg.conf (if anyone is trying to do the same thing, you will prob. have to change some values):
```

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    BusID        "PCI:0:16:0"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

```If something screws up and you can barely read your screen when you boot up, (hopefully you can read it at least a bit), then press ctrl-alt-F2 at the login screen, login to sudo move the radeon-kms.conf file to radeon-kms.conf.bak and sudo reboot.

---

### Post by Dukenukemx on 2010-05-01
Can someone explain how to fix this like zeroti did?  I have no idea how to create a radeon-kms.conf or a xorg.conf.

---

### Post by zeroti on 2010-05-01
> **Dukenukemx said:**
> Can someone explain how to fix this like zeroti did?  I have no idea how to create a radeon-kms.conf or a xorg.conf.

First we need to find out if you have a radeon card.. so check the results of:

```
lspci | grep ATI
``` in the terminal

If you do use a radeon card, then you can edit the radeon-kms.conf file to make the change. The thing is that I can point you towards some resources for the xorg.conf file, but I don't know why my setup works, i.e. what is essential and what is not... and in my case, not having one made things... tricky to recover.

to edit the conf file, type:

```
sudo pico /etc/modprobe.d/radeon-kms.conf
```

as a tip, when you're typing something out in the terminal, you can supply part of a word at a time and then hit tab to complete part or all of it. if you press tab a second time after the first one had no effect, then if there are possibilities, they will be displayed below. this works for commands, some command options and all file names. it's often important to do tab completion with file names so you make sure you get one that exists, so you don't make a new file that won't get recognized because it is spelled wrong. but in this case, i don't think that i had one of these files before i needed it. :)

then just copy and paste into the radeon-kms.conf :
```
options radeon modeset=0
```

ONLY do this once you've gotten an xorg.conf that you think will work. you still need to save it, and it will only go into effect upon your next boot.

Here's a resource on xorg.conf files, I remember finding more, but I don't know where they are now or how I came to them:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#xorg.conf](http://ubuntuguide.org/wiki/Ubuntu:Lucid#xorg.conf)
[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

The second one will tell you how to find the agpmode and gartsize you need.

One thing you need to do is convert the number at the beginning of lspci | grep ATI from hex to decimal and some punctuational changes and use it as a BusID... As a tip, here's the conversion for mine:
0000:00:10.0   ->   PCI:0:16:0

Other than that, you should change the the identifier for the driver if you are using a different one and also look up how to find the agpmode and gartsize for your graphics card.

to edit the xorg.conf, just do "sudo pico /etc/X11/xorg.conf" and paste in what I have below and make modifications.

once you are confident that everything is in good order, reboot. if the screen is all crazy, then you need to change the name of the radeon-kms.conf file so that when you reboot again, it will be ignored. once the login screen shows up, press ctrl-alt-F2 and then type your user name, enter, password, enter and then do: "sudo mv /etc/modprobe.d/radeon-kms.conf /etc/modprobe.d/radeon-kms.conf.bak" tab completion would be helpful since it would be hard to read. then type "sudo reboot" and you should get your computer back like it was before.

Good luck! if you need more help, just post a message here. I'm watching this thread although i might not be able to check back in a while after about an hour and a half from now. :)

---

### Post by Dukenukemx on 2010-05-01
Thanks zeroti, everything is working just fine.  I didn't have to change anything about your xorg.conf.  Same configuration as mine.

Plus, I learned some new useful terminal features for linux. :P

---

### Post by zeroti on 2010-05-01
> **Dukenukemx said:**
> Thanks zeroti, everything is working just fine.  I didn't have to change anything about your xorg.conf.  Same configuration as mine.

Plus, I learned some new useful terminal features for linux. :P

Great! :)

---

### Post by linuxopjemac on 2010-05-02
Thanks zeroti, I added this info to the general xorg.conf page

[http://mac.linux.be/content/cross-distribution-issues](http://mac.linux.be/content/cross-distribution-issues)
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

---

### Post by shongzah on 2010-05-10
I'm running a Mac G4 MDD tower.
<code>lspci | grep ATI
</code> produced an output of <code>0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)</code>. Zeroti's instructions fixed my problem too. Checking Normal or Extra in the Appearance->Visual Effects tab gave me a pop up saying "seaching for drivers" then it would strip the frames from my windows until I rebooted. If I wanted to change the appearance of Gnome-do, I got a message that said I had to activate compositing.

---

