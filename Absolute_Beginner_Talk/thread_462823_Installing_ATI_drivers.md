---
title: "Installing ATI drivers"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by darkoz on 2007-06-03
Hi all,

I just registered to share a few gems of wisdom with all you unfortunate sods with older ATI cards. I searched these forums (and the net) going far and wide and after several hours of screwin' around this is the only guide that helped me (i have an ATI 9200).

DISCLAIMER: I have searched the forums and i have read and tried all the guides on the wiki (including [this]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI") one). fglrx is a dog - i have never dealt with a lamer driver. I am also a proud linux noobie hence this is probably most appropriate for others like me.

The following is an excerpt from [here]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon").

> 
Please make sure that you have all updates installed on your Ubuntu Feisty Fawn desktop before you try this.
 
**Find Out About Your Graphic Card**

First you should find out about your graphic card. Open a terminal (Applications > Accessories > Terminal) and type

```
lspci
```

You should find something like this in the output:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)
```

(This output is from my notebook which uses an ATI Mobility Radeon 9200 graphic card.)

The following list shows which ATI graphic cards can use Beryl (your graphic card should be listed under Full 3D Support if you want to use Beryl):
 
Full 3D Support

    * 7000 / rv100 based cards.
    * 7200 / R100 based cards.
    * 7500 / rv200 based cards.
    * 8X00 / R200 based cards.
    * 9000 / rv250 based cards.
    * 9100 / R200 based cards.
    * 9200 / rv280 based cards.

 
Experimental 3D Acceleration

    * 9500 / R300 based cards.
    * 9600 / rv350 or rv360 based cards.
    * 9700 / R300 based cards.
    * 9800 / R350 or R360 based cards.
    * X300 / rv370 based cards.
    * X600 / rv380 based cards.
    * X700 / rv410 based cards.
    * X800 / R420 or R423 or R430 or R480 based cards.
    * X850 / R480 or R481 based cards.
 
2D Acceleration Only

    * Xpress 200M Northbridge integrated GPUs
 
Unsupported

    * X1300 / R515 based cards.
    * X1600 / R530 based cards.
    * X1800 / R520 based cards.
    * X1900 / R580 based cards.
 
**Configure AIGLX Plus The Open-Source ATI Driver**

We want to use AIGLX with open-source ATI driver instead of XGL with the proprietary ATI driver (fglrx). Therefore we have to disable fglrx. First we disable the fglrx kernel module:

```
sudo modprobe -r fglrx
```

Then we run

```
glxinfo | grep vendor
```

If you see ATI mentioned in the output, then you're still using the wrong driver. If you see SGI instead, everything's fine. On my notebook, the output looked like this:

```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```

If you have ATI in the output of the previous command, remove the fglrx driver like this (you can do this also if you have SGI in the output - just to go sure):

```
sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

Next we have to modify /etc/X11/xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

Replace

```
Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "ati"
        BusID                "PCI:1:0:0"
EndSection
```

with

```
Section "Device"
        Identifier        "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "radeon"
        BusID                "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection
```

(Please note the added Option lines and the changed Driver line. Of course, your Identifier will look different if you use a different graphic card than I do.)

The Monitor and Screen sections in /etc/X11/xorg.conf should be alright.

Also replace

```
Section "ServerLayout"
        Identifier        "Default Layout"
        Screen                "Default Screen"
        InputDevice        "Generic Keyboard"
        InputDevice        "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice        "Synaptics Touchpad"
EndSection
```

with

```
Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier        "Default Layout"
        Screen                "Default Screen"
        InputDevice        "Generic Keyboard"
        InputDevice        "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice        "Synaptics Touchpad"
EndSection
```

(Please note that I added an AIGLX Option line at the top.)

And finally add the following two sections to the end of /etc/X11/xorg.conf if they don't exist elsewhere in the file:

```
Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

To make the changes take effect, we must restart X. We can do this by pressing Ctrl-Alt-Backspace (if this doesn't work, reboot the system).

Afterwards, run

```
glxinfo | grep vendor
```

again. You should now see that SGI is mentioned in the output:

```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```

Then run

```
glxinfo | grep "direct rendering"
```

This should show the following line:

```
direct rendering: Yes
```


At this point you should have hardware 3d Acceleration (unless that last command says: "direct rendering: No"). Give yourself a pat on the back. 
Keep in mind that the guide this comes from also has 2 more pages of instruction on how to get Beryl working after this - which was also very useful.

Hope this all works out for y'all with ATI cards. 

Darko

EDIT: must learn to press preview before submit :)

---

### Post by stepper on 2007-06-03
It works for me, thank you man! :D

---

### Post by matteospqr on 2007-06-04
Hello!!

At the end I get 
direct rendering: No!!

What can I do?

---

### Post by tommybeeasy on 2007-06-04
Me too. I've followed every guide on these forums and my glxgears is giving me around 4800 fps. What am I doing wrong?

---

### Post by durfff on 2007-06-15
Have you guys made sure your fglrx drivers have been properly uninstalled? no errors output when running the command?

Also check your bios to check the speed of the AGP port (1, 2, 4, 8?) and take note of the FastWrite and other options -- make sure they match in your xorg.conf file.

After that [try the second page]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon_p2?") of the original tutorial:

The first part of the tutorial (loading modules) worked for me, gave me direct rendering: yes and installed beryl without a problem. The only thing is, my CPU is getting old (it's a Athlon 2600 XP+ but it got battered by 4 years of frequent 24-track music recording and other 140Mb Photoshop artwork lol - tis a bit fried) so I've gone with compiz alone instead, not too fancy but solid and smooth. 

Hope this helps a bit, if not it makes me feel good I've done it :-P

IM if you want info - I'd love to help!

---

### Post by lcarron000 on 2007-06-15
Worked just great 4 me :popcorn:. Beryl is fantastic, even considering my test machine is a Dell PowerEde 4300 Server. This is a very old machine so I wasn't looking for big results, but I must say things are better than I was looking forward to. I am getting absolutely no lag, even during intense use. specs: Dual 550 PIII CPU's | 1GB Ram | 256MB Ati Radeon 9250 PCI dual display. Really not much to work with. Here are some screenshots.

[IMG]http://farm2.static.flickr.com/1302/552243441_cf26fe7f75.jpg?v=0[/IMG]

[IMG]http://farm2.static.flickr.com/1245/552243407_247c837107.jpg?v=0[/IMG]

[IMG]http://farm2.static.flickr.com/1094/552243379_ac53c0a73f.jpg?v=0[/IMG]

[IMG]http://farm2.static.flickr.com/1101/552243349_0a26c99231.jpg?v=0[/IMG]

[IMG]http://farm2.static.flickr.com/1340/552243341_8d8d71abbe.jpg?v=0[/IMG]

Now I have to get the seconday to work. I will be using a 42" plasma via HDMI or s-video. I would like to beable to start a new X server using the secondary display, if it's at all possible. Any ideas or can anyone point me in the right direction.

---

### Post by frazelle09 on 2007-07-31
Thanks for the great tutorial!  However when i do the glxinfo i get...

razelle09@LindasLinux:~$ glxinfo | grep vendor
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Any ideas?  Have a great evening!  :)

Am using an ATI Radeon R250 card on this Gateway laptop which is running Freespire RC 1.9.14...

---

### Post by ItalOz on 2008-01-09
goooooood one,
it worked beautifully on my old ASUS laptop which has a [Radeon Mobility 7500] as graphic device.

I also added to the xorg.conf file the resolution I knew my card and screen could achieve (i knew it from Windows drivers) that is to say

Modes		"1400x1050"	"1024x768"	"800x600"	"640x480"

in the section "Screen"

and now I am running at 1400x1050 resolution.

By the way Envy didn't work for me.

ItalOz

---

### Post by matthewcraig on 2008-07-01
You may be interested in these Free Software (GPL) drivers being produced with cooperation with AMD and the Free Desktop Project.  "radeon" and "radeonHD" seek to produce 2D and 3D support for AMD's (was ATI) video cards:

[http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

Please note, these are still in development and so the processes are unsupported.  But, I am using the "radeonHD" and it is quite stable, but your experiences may vary.  I read they would be available and configured within the next version of Ubuntu, so you may want to wait another few months for a supported configuration.

---

