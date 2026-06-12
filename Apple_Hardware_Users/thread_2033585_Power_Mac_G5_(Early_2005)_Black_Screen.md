---
title: "Power Mac G5 (Early 2005) Black Screen"
date: 2012-07-26
forum: Apple Hardware Users
---

### Post by Trzone on 2012-07-26
I have browsed the forums quite a bit and have tried adding several options to yaboot.conf, running ybin -v afterwards

I can ssh into the Power Mac G5 (Early 2005) Specs below 
[https://en.wikipedia.org/wiki/Power_Mac_G5#Product_revision_history](https://en.wikipedia.org/wiki/Power_Mac_G5#Product_revision_history)

The graphics card: NVIDIA GeForce 6800 Ultra DDL

Before I installed the latest updates, I was able to boot up into a low bit display "quiet splash video=ofonly nouveau.modeset=0"

Now there's a brief flash of color and then it goes black.
Any suggestions?

---

### Post by tiresia on 2012-07-26
Does your Card have two DVI connections? Did you try to switch to the second one?

---

### Post by Trzone on 2012-07-26
I do have two dvi connectors, the one on the left works but the right one (haven't used before) only works up until yaboot.

There does not seem to be much information on the nvidia card but I am going to try some more options 

I could reinstall but it would be ~8 bit color depth before upgrading the drivers...

---

### Post by str8bs on 2012-07-26
The behavior you describe sounds a lot like a "phantom" port issue the FX5200 has.

The usual suspect is TV-1 but different cards can name ports differently.

I would first try these.
```
boot: Linux video=TV-1:d
or
boot: Linux nouveau.tv_disable=1
``` (replace Linux with live if using live iso.)

If it is a phantom port other than TV, the only way I have found to identify it is a pain. [_Link_]("http://www.mintppc.org/forums/viewtopic.php?f=15&t=810&start=10")

If yours does have this issue, would you mind sharing Xorg and dmesg logs? I am working on thorough documentation for a bug report. It is an interesting little bugger... Depending on what monitor is connected, what port, or whether an adapter is used, the result can range from no display, to poor display, to no problem.

EDIT: Forgot you mentioned SSH. A quick check would be```
cat /var/log/Xorg.0.log | grep -i connected
```

---

### Post by Trzone on 2012-07-27
Here are my Dmesg, Xorg.0.log and Xorg.0.log.old

(I added .doc due to forum limits, they are just txt)


There seems to be TV-1 and TV-2
NOUVEAU(0): Output DVI-I-1 connected
NOUVEAU(0): Output TV-1 connected
NOUVEAU(0): Output DVI-I-2 connected
NOUVEAU(0): Output TV-2 disconnected

Also, is there an integrated graphics card or is this what is allocated?

NOUVEAU(0): GART: 64MiB available

Linux nouveau.tv_disable=1 and Linux video=TV-1:d give me a cool checkerboard of purple, green, beige and brown :D 

I will try disabling other interfaces, dvi-I-1 etc and will look more at your posts at mint

Thanks

---

### Post by str8bs on 2012-07-27
Thanks for the logs. Looks like at least one of your problems is the same as mine. Times 2! I've never seen the checker board, but I would definitely rule out the phantom ports first.

I've learned a lot since writing that guide and am working on simplifying it. I would welcome any suggestions.
> Also, is there an integrated graphics card or is this what is allocated?

NOUVEAU(0): GART: 64MiB available
Not sure what you mean by that? Yes your card has GPU.  I'm still learning all this stuff, but my understanding is that GART is an address translation table used to access aperture. There is no need to change that usually. It is NOT the same as VRAM or aperture size.

EDIT: After further review of the logs I see a couple of other potential problems. There is a "resize called" in xorg log. That should go away once phantom ports are ruled out. If not, try forcing a mode with boot params or xorg.conf. I see in dmesg "AGP aperture ... @0x0" . To rule that out, append nouveau.agpmode=0 (forces PCI mode) to any other boot parameters you are using. If you get to a good boot, try upping that. (1,2,4,8)

---

### Post by Trzone on 2012-07-27
output of: cat /var/log/Xorg.0.log | grep -i connected

Output DVI-I-1 connected
Output TV-1 connected
Output DVI-I-2 connected
Output TV-2 disconnected 

I've also tried: append="video=DVI-I-1:1024x768:@60:-24" and
video=DVI-I-1:1600x1200:@60:-24 and more checkboards :D


TV-1 & 2 are confirmed phantom ports (no signal msg)
Disabling video=DVI-I-1:d or 2 results in a no signal msg
When either dvi is enabled I get the checker board :D

Just trying to get some thoughts / suggestions (verbose)

---

### Post by str8bs on 2012-07-27
Just to clarify. You are only connecting a display to DVI-I-2 ?
Is this 12.04?

My FX5200 has ADC port which is recognize as DVI-I-1. When facing the back on mine, that would be the port on the right. Yours may be opposite.

Are you using straight DVI to DVI cable? You might need to force digital with a capital D. IE: DVI-I-2:D

Are you combining appends to disable all phantom ports? example:```
boot: video=TV-1:d video=TV-2:d video=DVI-I-1:d nouveau.agpmode=0
```EDIT: Clarify "phantom port." I wouldn't call it a "phantom port" unless it sees a load and therefore registered as connected. Just seeing the port doesn't cause a problem, it's that registers a load and connects that creates the problem.  In your case, you have TV-1 plus either DVI-I-1 or DVI-I-2. Not sure which one the display is actually plugged it to.

---

### Post by Trzone on 2012-07-27
Yes I should have clarified: Ubuntu 12.04 ppc-64
I am using DVI-1-2 (when facing back, on the left) Should I be using DVI-I-2? 

I have tried the nouveau.agpmode=x with this appending:
"append="video=TV-2:d video=TV-1:d nouveau.agpmode=1"
As disabling dvi-I-1 or 2 results in a blank display

I will try with a capital D, I am using a straight dvi to dvi cable, will try all these commands with the cable in the dvi 1 spot(right when facing the back)

Thank you very much!

Output of xrandr: Can't open display 

So it seems that my display is not configured. I have tried this to no avail:

sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

**Display plugged into dvi-1 (when facing back, on the right) :D

---

### Post by str8bs on 2012-07-27
I'm assuming you are running xrandr via SSH? That won't work unless you take control of the right CRTC. Until we rule out phantom ports, it will be trial and error to find that.

Since you have SSH set up, I might try booting with your monitor disconnected and grep for connected. That might help you confirm what it is actually calling each port.

Also, make sure you use agpmode 0 until we get to a GUI. That will only impact performance and we can worry about last.

Running xorg configure IMO will be futile until we know we have eliminated phantom ports. I would recommend not adding xorg.conf to the picture either until phantom ports are confirmed ruled out (disabled.) That will make your logs very confusing.

The first goal we need to achieve is getting to only one port showing connected and confirming that is the same port your display is plugged in to.

---

### Post by str8bs on 2012-07-27
If it helps, the Xorg.0.log you attached was showing a Dell 2000FP connected to DVI-I-2.

 In theory, with the display connected to the same port as when you ran that log, one of these should work unless you have a secondary problem or it is also possible the card reports loads differently depending on what is plugged in.

```
Linux video=TV-1:d video=DVI-I-1:d video=DVI-I-2:e nouveau.agpmode=0
or
Linux video-TV-1:d video=DVI-I-1:d video=DVI-I-2:D nouveau.agpmode=0
```The first two disconnects (:d) should really only be the necessary entries because the monitor EDID seems to be reported correctly. Unless the ports are moving around on us (no idea how your card reacts to actual connected load per port,) or you have another issue, this should work:
```
Linux video=TV-1:d video=DVI-I-1:d nouveau.agpmode=0
```Just to be explicit, this would be my "Hale Mary" attempt:```
Linux video=TV-1:d video=TV-2:d video=DVI-I-1:d video=DVI-I-2:e nouveau.agpmode=0
```

If that doesn't work as far as eliminating phantom ports and agp issues, then I would speculate your card is A. doing something I haven't seen (IE: maybe disabling DVI-I-2 when TV-1 is disable or some other weirdness), or we have yet another unknown problem with that card.

Also, I'm assuming this is new install and you have not changed any blacklist settings.

---

### Post by Trzone on 2012-07-27
I have a new xorg.0.log file attached, I unplugged the monitor cable and now it shows as only the 2 dvi interfaces connected.
I was unable to disable either dvi as that turned off? both ports

cat /var/log/Xorg.0.log | grep -i connected
[    15.659] (II) NOUVEAU(0): Output DVI-I-1 connected
[    15.659] (II) NOUVEAU(0): Output TV-1 disconnected
[    15.659] (II) NOUVEAU(0): Output DVI-I-2 connected
[    15.659] (II) NOUVEAU(0): Output TV-2 disconnected

Is there a nvidia driver? I'd be fine with compiling it (sys admin)

---

### Post by str8bs on 2012-07-27
There is no proprietary driver. You could compile NV or just use FBDEV but you would be throwing away all of your GPU power. (There have been a lot of threads about issues with NV lately as well.)

I think that card was an early DUAL-link DVI to support the 30" Apple cinema displays. I wonder if that is why turning off either kills both?

I have an idea to work around it using xorg.conf. It will be late tonight before I can look at it further, or you can try it. Use "Option B" on the first page of that thread I linked combined with only:
```
Linux video=TV-1:d nouveau.agpmode=0
```Just to clarify one more time:
It works when plugged in to DVI-I-1 but not DVI-I-2.
You are only connecting one display and not trying multi-head.

---

### Post by Trzone on 2012-07-27
How would I use fbdev? We are using it as a basic computer, nothing fancy, so that would be helpful. 

Yes only 1 display, 1 port. I am only testing on dvi-1, unfortunately the display does not work for either ports. We are going to see if we can find a ati or other card to swap. 

Would I remove the xserver-xorg-nouveau package or is there more to this?

I tried the command suggested: video=TV-1:d nouveau.agpmode=0

I am stumped, thank you for being so patient :D

---

### Post by str8bs on 2012-07-27
I warned you phantom ports are a pain. There are two different ways I've seen that they can cause failure, the nastiest of which I think is what DVI-I-1 is causing you.

No need to completely yank out package nouveau.

  Have you tried plugged in to DVI-I-2 and only disabling TV-1? I am speculating that DVI-I-1 is the dual link port.

  The 8 bit color you see with nouveau.modeset=0 is actually using FBDEV. We should be able to correct color depth, but in my experience, it still involves a variation of that "Option B" I mentioned whether using NV or FBDEV.

  If you can hang tight, I'll make an xorg.conf that might work. We will need that anyway to correct color depth with FBDEV.

---

### Post by str8bs on 2012-07-27
OK. I did this quick so I hope I don't have type-o's.

In the very fist Xorg.0.log you attached, it looked like a DELL display was detected correctly. In the latest, the modelines look correct, but it does not report the EDID of the DELL. I think DVI-I-2 plugged to your display is our best bet due to that.

With display plugged in to DVI-I-2 (whichever port was connected when you created the first log), try this in this order.

1. create /etc/X11/xorg.conf like this:
```
Section "Device"
    Identifier    "6800"
    Driver        "nouveau"
    Option    "Monitor-DVI-I-1" "DVIport1" ##curse you!
    Option    "Monitor-DVI-I-2" "DVIport2"
    Option    "Monitor-TV-1" "TVport1"
    Option "Monitor-TV-2" "TVport2"
EndSection

Section "Monitor"
    Identifier    "DVIport2" #The one we are trying to see.
EndSection

Section "Monitor"
    Identifier    "DVIport1"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TVport1"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TVport2"
    Option    "Ignore" "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "6800"
        DefaultDepth    24
           SubSection        "Display"
             Depth         24
            #Virtual 1600 1400 #Remove # left of Virtual if corrupt graphics.
           EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

```2. ```
boot: Linux nouveau.agpmode=0
```3. If that doesn't work:
```
boot: Linux video=TV-1:d nouveau.agpmode=0
```4. If that doesn't work, change the "nouveau" next to "Driver" in xorg.conf to "fbdev" and then```
boot: Linux nouveau.modeset=0
```*If X doesn't start at all, I probably have a type-o.

EDIT: And I forgot 5. If THAT doesn't work, go find a hammer and... 
Kidding, that should always work. If not, post xorg log from there.

---

### Post by Trzone on 2012-07-30
When i use 'nouveau.agpmode=0', I get a quarter of the screen with the boot logo which then turns into the checkerboard.

In Xorg.0.log, this error is interesting 
No monitor specified for screen "Default Screen".
Using a default monitor configuration.

I have looked into including the busID in xorg.conf but that did not make a difference unfortunately. 
I'm going to try to change this to include the 'monitor'

Section "ServerLayout"
Monitor DVIport2

To see if that works.
I want to thank you for taking the time to create the xorg config and look over my logs. You have gone above and beyond! :D

---

### Post by str8bs on 2012-07-30
Hi, thanks for persisting.
Who's to know if the dev/s have the ability to fix this without breaking other cards (IE: non-appleized 6800) much less the time. I hope they can if we get enough info to them. You obviously have some Linux experience. If this were a person's first Linux experience, it might very well be their last.

I would try changing only the screen section from the previous xorg.conf to force the monitor, and then try that with display connected to each port. For now, lets just test with fbdev. (The word in quotes next to Driver should be "fbdev"

```
...
Section "Screen"
    Identifier    "Default Screen"
    Device        "6800"
    Monitor       "DVIport2"
        DefaultDepth    24
           SubSection        "Display"
             Depth         24
            #Virtual 1600 1400 #Remove # left of Virtual if corrupt graphics.
           EndSubSection
EndSection
...
```

I'll look at you log in more detail tonight and see if I can come up with any other ideas. I think you can see the root cause of the issue is the card is reporting connecting devices where they are not.

If we can make Linux ignore those ports while leaving one you are trying to use, we should be able to get there. Just booting straight Linux with no params should work with this config, but I think the "Dual-Link" supplying modes on two ports is creating a behavior I haven't seen before.

---

### Post by str8bs on 2012-07-30
Looking at your most recent log shows some hope!

It is seeing your monitor correctly, but still ddc probe reports the bogus modes from the card and is setting default resolution based on that. Contrary to my last post, nouveau was used here, so try that first.

```
...
[    15.705] (II) NOUVEAU(0): EDID for output DVI-I-2
[    15.705] (II) NOUVEAU(0): Manufacturer: DEL  Model: a003  Serial#: 808663372
[    15.705] (II) NOUVEAU(0): Year: 2002  Week: 49
[    15.705] (II) NOUVEAU(0): EDID Version: 1.3
[    15.705] (II) NOUVEAU(0): Digital Display Input
[    15.705] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 41  vert.: 31
[    15.705] (II) NOUVEAU(0): Gamma: 2.50
[    15.705] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
[    15.705] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.705] (II) NOUVEAU(0): First detailed timing is preferred mode
[    15.705] (II) NOUVEAU(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.590
[    15.705] (II) NOUVEAU(0): blueX: 0.149 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
[    15.705] (II) NOUVEAU(0): Supported established timings:
[    15.705] (II) NOUVEAU(0): 720x400@70Hz
[    15.705] (II) NOUVEAU(0): 640x480@60Hz
[    15.705] (II) NOUVEAU(0): 640x480@75Hz
[    15.705] (II) NOUVEAU(0): 800x600@60Hz
[    15.705] (II) NOUVEAU(0): 800x600@75Hz
[    15.705] (II) NOUVEAU(0): 1024x768@60Hz
[    15.705] (II) NOUVEAU(0): 1024x768@75Hz
[    15.705] (II) NOUVEAU(0): 1280x1024@75Hz
...
[    15.706] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    15.706] (II) NOUVEAU(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    15.706] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.706] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
...
[    15.706] (II) NOUVEAU(0): Output DVI-I-2 connected
[    15.706] (II) NOUVEAU(0): Using exact sizes for initial modes
[    15.706] (II) NOUVEAU(0): Output DVI-I-2 using initial mode 1600x1200
...

```

Try a variation on the earlier xorg.conf that attempts to force the mode, like:```
Section "Device"
    Identifier    "6800"
    Driver        "nouveau"
    Option    "Monitor-DVI-I-1" "DVIport1" ##curse you!
    Option    "Monitor-DVI-I-2" "DVIport2"
    Option    "Monitor-TV-1" "TVport1"
    Option    "Monitor-TV-2" "TVport2"
EndSection

Section "Monitor"
    Identifier    "DVIport2" #The one we are trying to see.
    Option "Preferredmode" "1280x1024"
EndSection

Section "Monitor"
    Identifier    "DVIport1"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TVport1"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TVport2"
    Option    "Ignore" "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "6800"
    Monitor       "DVIport2"
        DefaultDepth    24
           SubSection        "Display"
             Depth         24
             Modes "1280x1024" "1024x768" "800x600" "640x480" "720x400"
            #Virtual 1280 1280 #Remove # left of Virtual if corrupt graphics.
           EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by Trzone on 2012-07-30
If i replace the driver with fbdev, I get a quarter of the screen. However with nouveau the screen is a checkerboard. Looking at the logs, the screen resolution isn't being set correctly (ddc)


"NOUVEAU(0): Option "Preferredmode" is not used":

Now I see what you mean, the config is being ignored.

We are getting close, I will attach the logs

---

### Post by str8bs on 2012-07-30
I expect if you had a 30" Apple Cinema display, this would have worked out of the box based on the modes reported with no monitor connected.

  Just to make sure I'm on the same page.
1.Boot with no params. xorg.conf Driver = nouveau = checkerboard
2. Boot with no params. xorg.conf Driver =fbdev = quarter of actual Ubuntu login screen.
The above 2 repeat regardless of physical connector attached to monitor.

Documentation is scarce, so this is a shot in the dark:
```
boot: Linux nouveau.duallink=0
```that is assuming the default is 1. You can try that too. I'm hoping that this might "separate" the dual link and make it treat the ports independently.

---

### Post by Trzone on 2012-07-31
I tried a different monitor and cable, but to no avail. 
You are correct, with nouveau, I get the checkerboard, fbdev is the small screen sometimes "low graphics drive".(no options enabled)

I tried adding this to yaboot.conf and it changed the resolution:
append="video=DVI-I-2:1280x1024@60"

Perhaps this would force the resolution? Or is the resolution not the issue?

Edit:

I have tried a few modelines in the Monitor section, while this doesnt give me any errors, I get a black screen (using nouveau)

Using the fbdev driver, I am able to get a larger screen with VirtualVirtual 1680 1050 however the screen moves around (when the cursor moves to the right or bottom of the screen) around where the 720x576 default resolution ends
It gives me an error message upon login: 
Cannot apply the stored config for monitors
crtc 262: trying mode 1680x1050@0hz with output at 1280x1024@0hz

Any thoughts?

---

### Post by Trzone on 2012-07-31
I forgot to add the configuration I am using (posting rather than a edit)

```
Section "Device"
    Identifier    "6800"
    Driver        "fbdev"
    Option    "Monitor-DVI-I-1" "DVIport1" ##curse you!
    Option    "Monitor-DVI-I-2" "DVIport2"
    Option    "Monitor-TV-1" "TVport1"
    Option    "Monitor-TV-2" "TVport2"
EndSection

Section "Monitor"
    Identifier    "DVIport2" #The one we are trying to see.
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
EndSection

Section "Monitor"
    Identifier    "DVIport1"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TVport1"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TVport2"
    Option    "Ignore" "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "6800"
    Monitor       "DVIport2"
        DefaultDepth    24
           SubSection        "Display"
             Depth         24
#	Modes "1600"
            Virtual 1680 1050 #Remove # left of Virtual if corrupt graphics.
           EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

---

### Post by str8bs on 2012-07-31
I'm just thinking out lout right now, I'll look at the logs again when I get a chance.

Sounds close with FBDEV but it is still thinking "multi-head" and setting up a large desktop? If you CTL+ALT+F1 from there do you see your console?

1. I probably confused things with that Virtual entry. Leave that commented out. I was thinking ahead to an unrelated acceleration bug that you may see if we get it working with nouveau. Not an issue with FBDEV.

2. I was going to suggest the modeline approach you tried. I'm confused by the mode though. What monitors are we using? I'm just wanting to look up and verify supported modes. You may have already done that.

3. Did that nouveau.duallink=0 param change anything at all? I would be curious if we removed/renamed the xorg.conf, boot with no params and no montior, and grep for connected with that switch if anything changes. I was hoping it might let us disable one without the other. I haven't found a lot of information on it. [http://comments.gmane.org/gmane.comp.freedesktop.xorg.nouveau/3491](http://comments.gmane.org/gmane.comp.freedesktop.xorg.nouveau/3491)

---

### Post by Trzone on 2012-07-31
I think fbdev is somehow extending the display 'virtual screen' i'm not sure how that works, but if it worked outside of the small 576x700 ish window, it would be fine. 


2. I switched to a dell p2210, it was more convenient and similar to the ones we will be using. I used cvt which is the way I got modelines (and looked in xorg.0.log) though all entries were slightly different. I will look up the modes (I see 1680 1050 on the monitor). 

3. With the xorg.conf moved, no monitor and only nouveau.duallink=0:

Output DVI-I-1 connected
Output TV-1 connected
Output DVI-I-2 disconnected
Output TV-2 disconnected

TV-2 has always been disconnected, while the other three were on/off.

Edit: When using fbdev, my cursor always stays within the small 720x576 resolution,
It has to do with the stretching of the screen, also 720x576 must be a default, i'll try to find the config file.

---

### Post by str8bs on 2012-07-31
Interesting. That may be a good sign. Compared to the output you got in post #12 of this thread (showed load on DVI 1 and 2 with no physical monitor) that would lead me to think that it should be able to correctly probe your monitor on one of the physical ports without combining the bogus probes.

My inclination from here would be the following:
1. With no xorg.conf, try the monitor on each physical port with that duallink=0 and see if disabling 1 still kills both. IE:```
Linux nouveau.duallink=0 video=DVI-I-1:d video=TV-1:d
```

or

2. Revert to our xorg.conf that attempts to do the same (using either FBDEV or nouveau) and remove anything that tries to force modes and boot with only:
```
Linux nouveau.duallink=0 video=TV-1:d
``` to see if we get accurate DDC probe of your monitor on DVI-I-2 and NOT the bogus modes that are fighting us.

PS: You are a trooper!

---

### Post by Trzone on 2012-07-31
I've been using this site for more info on xorg.conf:
[http://www.xfree86.org/4.1.0/XF86Config.5.html](http://www.xfree86.org/4.1.0/XF86Config.5.html)

This xorg.conf displays no devices connected / disconnected
cat /var/log/Xorg.0.log | grep -i connected

```
Section "Device"
    Identifier    "6800"
    Driver        "fbdev"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "6800"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
EndSection
```

The (--) means that it is a 'probed' configuration, it is getting the wrong information, ignoring the config. That is the real problem, yet it may also be freaking out over the dual link capability. If I can get the resolution set, then this should work hopefully :D

hardware: nouveaufb (video memory: 7088kB)
FBDEV(0): checking modes against framebuffer device...
FBDEV(0): checking modes against monitor...
FBDEV(0): Virtual size is 720x576 (pitch 720)
FBDEV(0):  Built-in mode "current"

---

### Post by str8bs on 2012-07-31
no, nouveau is integrated in the kernel which is what you are disabling with nouveau.modeset=0

EDIT: I should clarify that, because it can be confusing: something has to assign port/address information to whatever driver you specify. The default for nvidia built in the kernel is nouveau. You can still use FBDEV driver when booting with nouveau. Just to give an extreme example on my FX5200 with KMS(nouveau) enabled booting only with video=TV-1:d assuming I have all three open source drivers installed, this is what would happen.
1. Boots fine using nouveau. apt-get remove x....nouveau.
2. Boots fine using NV (when it was working) apt-get remove x....nv
3. Boots fine using FBDEV

Phantom ports can cause failure in a couple of ways.
1. Monitor 0 gets assigned to physical port that does not exist. The machine boots fine but sets your actual active display to off.
2. Monitor 0 gets assigned to the screen you are using, but modes are "combined" with those from phantom which can result in blank screen or poor screen depending on the modes supported by the monitor.
3. Your dual link issue seems to be forcing an explicit mode based on the phantom DVI.
The key seems to be A. Making the system ignore the phantom or B. Forcing a mode out all ports that fits your monitor.

EndEdit.

No idea how your card will react due to the dual link issue, but in addition to the routes in my previous post you could try:

edit /etc/modprobe.d/blacklist-framebuffer.conf and comment (#) nvidiafb
create a minimal xorg.conf like: (edit modes to reflect those supported by your monitor)
```
Section "Device"
   Identifier  "MakeItWork"
   Driver      "fbdev"
EndSection

Section "Monitor"
   Identifier   "JustWannaSeeAScreen"
EndSection
   
Section "Screen"
    Identifier "MyScreen"
    Monitor "JustWannaSeeAScreen"
    DefaultDepth 16 #If this works, try changing to 24.
    SubSection "Display"
        Depth 24
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    SubSection "Display"
        Depth 16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```and then boot:
```
[s]Linux nouveau.modeset=0 video=nvidiafb:XresYres-24@60[/s]
```replace XresYres-24@60 with your monitors native display resolution and rate.

EDIT: Forgot my append in yaboot. I still have to disable phantoms.

---

### Post by Trzone on 2012-07-31
Is this the correct syntax? (in yaboot.conf)
append="nouveau.modeset=0 video=nvidiafb:1680x1050-24@75"
```
mode "640x480" test failed
checking modes against monitor...
Virtual size is 1680x1050 (pitch 1680)
Built-in mode "current": 100.0 MHz, 58.1 kHz, 53.3 Hz
```


Edit: Too much information. It tests all the modes, now I am testing other things. Only a plain config will work (I will try to test the color depth, etc) I am kind of back where I started, but at least the nouveau driver is disabled
Here is my xorg.conf, attached a screenshot of my desktop :)


```
Section "Device"
    Identifier    "6800"
    Driver        "fbdev"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "6800"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
EndSection
```

Edit: Better news
This line gives me a full desktop background but it turns black every 10 seconds (refreshes) 
	append="nouveau.modeset=1 video=nvidiafb:1680x1050-24@60 video=DVI-I-1:d video=TV-1:d video=TV-2:d"

I'll try a lower mode, also I get 
CRTC 262: trying mode 1680x1050@0hz (I think that is the dcc's config)

"Default Screen" for depth/fbbpp 24/32
Thank you for helping me get this far!

---

### Post by str8bs on 2012-07-31
I'm stumped as far as how the dual link  issue might change things.  I just re-tested on mine and I was _wrong_. (I'll strike through my previous.) Forcing nvidiafb still gets me phantom port issues so I have to video=TV-1:d.  I'm stumped as to how to make yours ignore the offending load on DVI.

With KMS enabled, I can boot FBDEV at 24 bit no problem.

Did booting with nouveau.duallink=0 video=DVI-I-1:d video=TV-1:d with driver fbdev in xorg.conf and no modes reveal anything? On either physical connector?

---

### Post by Trzone on 2012-07-31
What is KMS? 

cat /var/log/Xorg.0.log | grep -i connected doesn't show anything with  these two:
```

nouveau.duallink=0 video=DVI-I-1:d video=TV-1:d and same with
nouveau.modeset=1 video=nvidiafb:1680x1050-24@60 video=DVI-I-1:d video=TV-1:d video=TV-2:d"
```



I think I saw something in the logs, how would I find out how much VRAM the driver is using / capable of using? I saw 8MB somewhere :D

---

### Post by str8bs on 2012-07-31
I think we just created another framebuffer running on another "device" if you check the logs.
specifying nouveau.modeset=1 is the same as omitting nouveau.modeset=0 AFAIK (on is default)

---

### Post by Trzone on 2012-07-31
I tried this (omitting modeset)
append="video=nvidiafb:1680x1050-24@60 video=DVI-I-1:d video=TV-1:d video=TV-2:d"

I get the same issue, I'm leaving work now, but i'm glad we made some progress.

Here are my logs:

---

### Post by str8bs on 2012-07-31
I think we just created another framebuffer running on another "device" if you check the logs.
specifying nouveau.modeset=1 is the same as omitting nouveau.modeset=0 AFAIK (on is default)

KMS is Kernel Mode setting which is why nouveau is integrated in the kernel.

> at /var/log/Xorg.0.log | grep -i connected doesn't show anything with  these two:
     Code:
     nouveau.duallink=0 video=DVI-I-1:d video=TV-1:d
 and that is both with and without the monitor connected to either port?

Did you also try reverting to the first xorg.conf I posted and using nouveau.duallink=0? 

I'm stumped. Definitely bug report time. If we could just get it to ignore both phantom ports that you see with duallink=0 (DVI-1 and TV-1) then you should be good to go with either driver.
You could try compiling and installing NV and see if it will play nice with your card. [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics ]("https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics")
scroll down to nvidia. You will want to boot with nouveau.modeset=0 if you go that route.

EDIT: Just saw your last. I'll look at logs and see if I can think of something. I'm stumped ATM.

---

### Post by Trzone on 2012-07-31
When I am using fbdev, I can't add anything to the basic configuration (xorg.conf post 27) otherwise it gives me a blue screen with a xserver error prompt, really low res)

I was looking back at the first xorg.conf post #16, I'm not sure if I have changed it back to nouveau and tested it with nvidiafb yaboot parameter.  

Also is this the correct? Or do I omit the 24?
video=nvidiafb:1680x1050-24@75

I may reinstall tomorrow to make sure that reconfiguring xserver and other packages can't affect this.

Do you think that I would have better luck compiling nouveau?

Edit: I am looking back at your posts on mintppc, I may have to add the bus ID, and use a square virtual host while also adding the resolution to yaboot. 
I'll work on this tmrw, I need a break

btw, Thanks

Edit: I have been using nouveau.duallink=0

---

### Post by str8bs on 2012-07-31
> **Trzone said:**
> 

I was looking back at the first xorg.conf post #16, I'm not sure if I have changed it back to nouveau and tested it with nvidiafb yaboot parameter.  

I may reinstall tomorrow to make sure that reconfiguring xserver and other packages can't affect this.

Do you think that I would have better luck compiling nouveau?

Edit: I am looking back at your posts on mintppc, I may have to add the bus ID, and use a square virtual host while also adding the resolution to yaboot. 
I'll work on this tmrw, I need a break

btw, Thanks


Definitely take a break.  I recommend- don't get caught up in the voodoo of xorg.conf.  Bus ID should not be needed. Your card is found without issue. You may be seeing a new "card" showing up with a strange ID. That is likely the 2nd framebuffer we added which is why I try to avoid xorg.conf when possible. The virtual workaround is also a non-issue for now. That is related only to an acceleration bug which won't come in to play until you get a valid screen.

Just to revisit what is happening. With no monitor connected, Linux boots perfectly fine and is outputting a display on a device that does not exist thanks to the "phantom" loads that look like they fit a 30" cinema display (Thanks Apple.) 

The only way I've defeated this issue in the past is by telling Linux to ignore those bogus "displays" regardless of the driver used. The dual-link your card has seems to be complicating that issue.

I know on mine, the order in which it assigns monitors changes depending on whether I use a straight DVI cable or DVI to VGA adapter.

Just IMO, but compiling or reconfiguring likely won't get us anywhere because the issue is that the HARDWARE (the card) is supplying those bogus modes.

If anyone else is reading this and has ideas, please chime in.

---

### Post by str8bs on 2012-08-01
I'm starting to think the hammer was a good idea. Kidding.

From your last kernel log. Everything we want disabled gets disabled, but then a load keeps being detected. I'm guessing that is when you see the refresh every 10 seconds.

```
[drm] forcing DVI-I-1 connector OFF
 [drm] forcing TV-1 connector OFF
 [drm] forcing TV-2 connector OFF
...
[drm] nouveau 0000:f0:10.0: Output DVI-I-2 is running on CRTC 1 using output B
...
Load detected on output A
[drm] nouveau 0000:f0:10.0: Setting dpms mode 3 on tmds encoder (output 4)
[drm] nouveau 0000:f0:10.0: Setting dpms mode 0 on tmds encoder (output 4)
[drm] nouveau 0000:f0:10.0: Output DVI-I-2 is running on CRTC 1 using output B
 [drm] nouveau 0000:f0:10.0: Load detected on output A
```

I'm stumped. If you are thinking of installing again anyway, you may want to try 10.04. IIRC, it has KMS enabled out of the box but uses NV (and that version worked fine on mine.) I wouldn't bank on it though.

For grins, have you tried putting an actual load on both ports to see what happens? IE: monitor on both DVI ports and video=TV-1:d

---

### Post by Trzone on 2012-08-01
Well a dual monitor setup works fine :D

I still get this error (It's a popup at login as well)(trying to apply a resolution at 0Hz)
[drm] nouveau 0000:f0:10.0: Output DVI-I-2 is running on CRTC 1 using output B

I am unable to apply a custom resolution but that is alright at the moment
This code works fine with a dual monitor setup and with a single monitor as well.
```
append="video=TV-1:d video=TV-2:d"
```

But fails if I disable DVI-I-1 or DVI-I-2 (we saw that earlier)

By trying a dual monitor setup, the video card and nouveau drivers are recognizing either monitor / port.

---

### Post by str8bs on 2012-08-01
> **
Edit:
This code works fine with a dual monitor setup
     Code:
     append="video=TV-1:d video=TV-2:d" 
Removing that line gives me one monitor with a quarter of the screen (fbdev)
TV-1d and TV-2 are phantom ports, dvi-I-1/2 are usable (if i disable one,  I can see the other) :) I thought the card might stop reporting false loads on both DVI if they had real ones. Just tell the boss everyone needs dual monitors.
For changing resolution, are you using xrandr?

---

### Post by Trzone on 2012-08-01
I think I could set a custom res with xrandr, but so far it is recognizing it automatically.
The last thing to do is get rid of that weird error when logging in


```
Could not apply the stored configuration for monitors:
Trying modes for CRTC 262 
mode 1680x1050@0Hz with output at 1600x1050@0hz
```

Is it trying to shrink to the monitor's size? (It's a 1680x1050@60hz monitor though)

---

### Post by str8bs on 2012-08-01
I would be concerned that the DVI phantom pain may return after a cold boot or some other hardware reset. If you have any laying around, simply plugging a DVI to TV (rca) adapter to the dual link port may prevent those DVI "phantom" modes from presenting and then you would just have to disable TV in software.

error message- This is speculation.
I have seen several bug reports that are not "failures" but "nuisance" that may be related and I think is part of ONE of the causes of failure with phantom ports. In multi-head setups, the default seems to try to force all screens to one resolution instead of setting each independently to display native. You might be able to play with multi-head setups via xorg.conf to get around that. Check for RANDR wiki's.

One test might be: Plug in two identical monitors and test with and without the duallink=0 to see if that error goes away.

Good work. Glad you are finally getting to see a screen.

---

### Post by Trzone on 2012-08-01
Fortunately, the message only displays itself to a admin user! So we are all good.
I want to thank you for taking the time and making all those suggestions / configs. Usually a dual monitor setup would be the last step but oddly enough it is what fixed the problem.

Note to all: Disable 'phantom' TV-1 or TV-2 ports

My /etc/yaboot.conf append line
	append="video=TV-1:d video=TV-2:d quiet splash"

Xorg.conf should only be used if necessary (avoid it, or using complex configurations)

The xorg.conf that worked for me:
```
 Section "Device"
    Identifier    "6800"
    Driver        "fbdev"

EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "6800"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
EndSection
```

Links:
[https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics)
[http://www.xfree86.org/4.1.0/XF86Config.5.html](http://www.xfree86.org/4.1.0/XF86Config.5.html)

---

### Post by str8bs on 2012-08-01
Great news.
> **Trzone said:**
> 
Xorg.conf should only be used if necessary (avoid it, or using complex configurations)

[]("http://www.xfree86.org/4.1.0/XF86Config.5.html") +1

Until if/when we can get a patch to work around these, I think I will start a post somewhere that lists cards with known phantom ports so others might avoid the pain. For clarity, could you confirm your physical set up that is working with this config?
IE: When facing the back, which port left or right? Using straight cable or adapters? Monitor model that you are currently using.

Thanks

---

### Post by Trzone on 2012-08-01
When facing the back, the left port (DVI-I-2)

Using straight Cables (DVI to DVI)

Monitor: Dell P2210

---

### Post by Trzone on 2012-08-02
The Power Mac G5 (Late 2005) nVidia GeForce 6600, works on DVI-I-1 out of the box. 

But not DVI-I2 and there is only 1 phantom port: TV-1

At the moment I can only get 'flawless' graphics on unity 2D, on unity it whites out the sidebar + leaves a line around the wallpaper. Is there an option for graphics acceleration?

***Solved the 'whiteout of the sidebar' for unity(Still curious about acceleration)
yaboot.conf: 	append="quiet splash"

/etc/X11/xorg.conf
```
 Section "Device"
    Identifier    "6600"
    Driver        "fbdev"

EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "6600"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
EndSection
```

Thanks to str8bs!

---

### Post by str8bs on 2012-08-02
I'm confused. Is this a different machine? Or, did you change cards from 6800 to 6600?
 
You won't get any hardware acceleration with the FBDEV driver. Nouveau is necessary for that. However, the symptoms you describe in unity 3D sound acceleration related. I think quiet splash should only affect what you see during boot, not after desktop loads. 

```
xrandr -q
``` shows only 1 connected? 

```
glxinfo | grep render
``` to check for software vs. hardware acceleration

---

### Post by Trzone on 2012-08-02
It's a different machine, the 2005 "quad core" powermac G5. I am using the fbdev drivers, tomorrow I will try the nouveau in the same config.

---

### Post by str8bs on 2012-08-03
Interesting.I've learned from this.
Forum member ImaliveG5 in [ this thread ]("http://ubuntuforums.org/showthread.php?t=2030184&page=2")had 6600LE (same series but not identical to yours) and no phantom.

I am thinking these little buggers move around and/or disappear depending on which port you put a real display on and whether an adapter is used.  I think I led you astray on the 6800 by having you check with no display connected. The xorg.conf and assumptions made after that were based on what we saw then and I would speculate that is why you ended up with strange results. And, as you noticed, adding even a simple xorg.conf to a phantom port situation will mess with your head. :)

To try to clarify specific to your earlier 6800:
With no display connected, it obviously showed loads on DVI-1 and 2 and only TV-1. With the display connected on DVI-I-2, you ended up with phantoms actually on TV-1 and TV-2.

If I could start over again. I would definitely leave xorg.conf out of the picture until a last resort and instead:
1. Follow the Step by Step with display connected (using grep to speed things up) and use ONLY boot params to attempt disable.
2. If unsuccessful, SWAP ports and repeat the process.

With the simple xorg.conf you have now, it is possible that you still have a "phantom" port and IT is using FBDEV, but the display you see is using nouveau and that could explain why you saw acceleration related "bugs." You should see that in Xorg.0.log if so.

Specific to the possible acceleration related bugs, there are a few workarounds but they vary for different cards. Some can get around just by choosing Unity 2D at log in. If you then have graphics corruption on only the lower part of screen, see [this thread.]("http://ubuntuforums.org/showthread.php?t=1937940&page=2")

---

