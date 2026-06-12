---
title: "Can't change refresh rate, can someone check my Xconf please? :) (1st post!)"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Caracal on 2006-12-15
Hey everyone, please be gentle, this is the first time i've really made an effort with any linux distro, and this is my first post! :D

Anyways, i'm trying to change my refresh rate to 85Hz (I've managed to 'enable' the resolution i want) but no matter what i seem to do, i can't seem to change it. 

I've already checked the guide [>here<](http://ubuntuforums.org/showthread.php?t=83973) and ...... well i'm not sure what to do now!

This is my current Xconf:

```
Section "Monitor"
    Identifier     "Iiyama"
    HorizSync       28.0 - 91.72
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
 Modeline "1280x1024" 185.64  1280 1376 1600 2024  1024 1024 1028 1079

EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Monitor        "Iiyama"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection    "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Maybe i've missed something silly..... i'm not sure (maybe something do with the 'modeline' part i added?) but i can't wait to fix this, because using   a 21" monitor @ 60Hz is giving me a headache... quite literally!

I haven't really messed around with any other options, except installing the latest nvidia drivers, using the envy script.

Any help would be gratefully appreciated! :)

Thanks

---

### Post by kerry_s on 2006-12-15
How about try not giving it a choice of ranges->
    HorizSync        85.0
    VertRefresh     85.0

---

### Post by Caracal on 2006-12-15
Wouldn't that be: 

 HorizSync       91.72 - 91.72
 VertRefresh     85.0 - 85.0        ?

---

### Post by Kazna on 2006-12-15
In System>Preferences>Screen Resolution:
Change your resolution to something different, set it and then check again and your refresh rate will usually have more/less options. It depends on what is chosen. 
19 inch screen @ 1280x1024 I only get 87 and 60 as options whereas I want 75Hz. @ 1024x768 I get 5 options from 60-85Hz etc

Sorry if this doesn't help :)

---

### Post by johnrh on 2006-12-16
Don't know if you've solved this yet, but maybe this works. Here are some extracts from my xorg.conf...

Section "Monitor"
	Identifier	"Philips 107T"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

The HorizSync & VertRefresh values come from my monitor's manual. I'm suspicious of your "modeline", not sure you need it. But don't take my word for that!

Here's how I've set my resolution & refresh rate...

SubSection "Display"
		Depth		24
		Modes		"1024x768_75" "800x600" "640x480"
	EndSubSection

You can see the _75 that sets the refresh rate for the resolution I'm using. 

All I can say is it works for me, if you want to try it. Keep us informed!

---

### Post by Caracal on 2006-12-16
OK i've spent the last few hours fidding around with this and i still can't get it to work ARGH :evil: 

I tried putting _85 after the resolutions, doing so, made all my resolutions disappear from the 'screen resolution' screen :/

This is how my xorg.conf looks right now, and i STILL can't select 85Hz :(

```

Section "Monitor"

	Identifier   "A102GT"

	VendorName   "Idek Iiyama"

	ModelName    "Iiyama A102GT, VisionMasterPro 502"

	HorizSync    27.0 - 110.0

	VertRefresh  50.0 - 160.0

	Option	 "DPMS"

EndSection







Section "Device"

    Identifier     "NVIDIA Corporation NV20 [GeForce3 Ti 200]"

    Driver         "nvidia"

EndSection



Section "Screen"

    Identifier     "Default Screen"

    Device         "NVIDIA Corporation NV20 [GeForce3 Ti 200]"

    Monitor        "A102GT"

    DefaultDepth    24

    SubSection     "Display"

        Depth       1

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       4

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       8

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       15

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection     "Display"

        Depth       16

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

    SubSection    "Display"

        Depth       24

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection

EndSection



Section "Extensions"

    Option         "Composite" "Enable"

EndSection



```

---

### Post by Yfrwlf on 2006-12-16
Perhaps you should start from a lower resolution to make sure it's supported?  First, I'd try narrowing the problem down, like making sure your xorg.conf settings really do HAVE the power to change things.  I'm a newb too mostly, but I've found it frustrating when xorg.conf changes dont' seem to do anything.  So, how about trying the following.  In the section:```
SubSection    "Display"

        Depth       24

        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

    EndSubSection
```Try seeing if changes there are actually doing something, what about trying changing it to this:```
SubSection    "Display"

        Depth       24

        Modes      "1280x1024_75" "1024x768" "800x600" "640x480"

    EndSubSection
```1280x1024 is an easier-to-handle resolution, and 75 Hz is higher than 50, so it shouldn't look *incredibly* flickery like I imagine it does to you now.  If that works, you'll be able to see the improvement, and you'll also know that those changes you are making to xorg.conf are actually doing stuff.  If it won't even support that resolution and refresh rate, there's something else that's very odd going on.

Also just to note, I don't know if this will effect anything or not, but Caracal used a script in order to install his drivers.  Caracal: If you tried changing the driver from "nvidia" to "nv" I wonder if that would make any more options available.  These are just random ideas to try, I have no idea what the problem actually is here.

---

### Post by Yfrwlf on 2006-12-16
After skimming some other threads where people are having the same problems with changes in xorg.conf not actually changing the screen resolutions or refresh rates, the only solution I've stumbled upon so far is that a change in drivers sometimes fixes the problem.  It may be then that the nvidia driver you are using isn't compatible with your monitor.  So, first I'd try using the nv driver, and if that does change things for you, you'll know the nvidia driver you installed quite frankly sucks.  Maybe it was even a beta driver.  Since it was a script, who knows.  Of course, you can check the version of it if you're curious, but if changing it to nv helps, I'd uninstall that nvidia driver if possible, and then try to install the nvidia driver from the Ubuntu Synaptic repositories instead.  Perhaps it works better, and perhaps that's why it's still being distributed through Synaptic even though it's an older driver?  Let me know if that helps, Cara. :)

---

### Post by Yfrwlf on 2006-12-16
Oh, and to help others help you, they might be interested in seeing your xorg log if it still doesn't work for you.  it's in /var/log/Xorg.0.log and, I'm taking this code from someone else's problem, but you might want to post any section that looks like this:```
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=46909632846912; xclk=20500
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction ( 1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): 570V TFT: Using default hsync range of 28.00-33.00 kHz
(II) RADEON(0): 570V TFT: Using default vrefresh range of 43.00-72.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
(II) RADEON(0): Not using default mode "640x350" (hsync out of range)
(II) RADEON(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (hsync out of range)
(II) RADEON(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (hsync out of range)
(II) RADEON(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (hsync out of range)
(II) RADEON(0): Not using default mode "400x300" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
(II) RADEON(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
(II) RADEON(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
(II) RADEON(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "832x624" (hsync out of range)
(II) RADEON(0): Not using default mode "416x312" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x768" (hsync out of range)
(II) RADEON(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (hsync out of range)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (hsync out of range)
(II) RADEON(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
(II) RADEON(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using mode "1024x768" (no mode of this name)
(II) RADEON(0): Not using mode "832x624" (no mode of this name)
(II) RADEON(0): Not using mode "800x600" (no mode of this name)
(II) RADEON(0): Not using mode "720x400" (no mode of this name)
(--) RADEON(0): Virtual size is 640x480 (pitch 640)
(**) RADEON(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(==) RADEON(0): DPI set to (75, 75)
```Post stuff like that and anything else that might be useful from your log.  That way you'll (and others) be able to see what Xorg is doing hopefully. :)

---

### Post by alienexplorers on 2006-12-16
Try this modline and see if it works:

Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync

---

### Post by Caracal on 2006-12-17
Thanks for all your replies :D

I just tried using that modeline, and it wouldn't load at all, so i had to revert to a backup conf :/

I'm using version 1.0-9631 nvidia drivers.. and i'm tempted to try uninstalling them and trying some others maybe... i dunno.

Gah this is so frustrating! it's just a simple resolution/refresh rate config... why won't it work lol ](*,) 

Can i just install the driver from add/remove, or do i need to uninstall my current drivers first?

Thanks >.<

EDIT: oh and i just uninstalled the Envy script... although i still don't know where/how to unstall my current nvidia drivers :D

---

### Post by Caracal on 2006-12-17
I'm close to giving up now, no matter what changes i make, it seems to either have NO effect, or some random affect when i go to 'screen resolution'.

---

### Post by Caracal on 2006-12-18
Right OK i'm not willing to give up just yet... i'm not going to let something as simple as changing the resolution/refresh rate, beat me!

I've tried lots of different configurations now. I've tried forcing my monitor to use only 85Hz (that didn't work, i was forced to the console when i rebooted).

I've tried manually changing my monitor identifer to 'Iiyama' that also didn't work. I then did some hunting around, and found someones Redhat config, using my monitor, so i did come copying and pasting and that didn't work either (i've confirmed my monitors horizontal freq. is 27.0 - 110kHz, vert. 50 - 160Hz) so i know that '*that*' part is correct.

The actual "ID" for my monitor is A102GT, and ive tried using that in my xorg, but that didnt have any effect either. Does the ID have to specifically match my exact monitor, or is it just used as a reference point by other drivers like the display drivers?

I think i tired using the 'nv' driver, and again, when i restarted X, it just forced me back to the console.

I've uninstalled the nvidia drivers via Envy, and again, on reboot, i had no GUI, and was forced back into the console, so at the moment, i've reinstalled the drivers (1.0-9631).

I'm pretty sure i SHOULDN'T be using the legacy drivers (i'm using a Geforce3 Ti200, which 'just' qualifies as  non-legacy lol).

I seem to get different available options between the nVidia x-serv options, and the 'screen resolution' screen... but either way, i haven't seen 85Hz as an available option ANYWHERE yet :( The best i can manage currently is 1024x768 @ 75Hz

Ohh and i've also tried what someone suggested earlier, of putting a "1280x1024_85" and that gave me an error when i loaded X, something about and error in line xxxx, so i assumed it was the line i just added.

Anyway, i've put my old xorg.conf below. The hashed out part of my config is something i tried earlier, but i've left it in there so you can see what i tried....

I hope someone can help, because this is stopping me from using my first linux distro! If i can't get this working im going to try Fedora... and if i get the same problem with that... well...  i just hope there's no one standing outside my window, because they'll be saying hello to a flying 21" CRT!

```

#Section "Monitor"
#    Identifier     "Iiyama"
#    HorizSync       28.0 - 91.72
#    VertRefresh     43.0 - 85.0
#    Option         "DPMS"
# Modeline "1280x1024" 185.64  1280 1376 1600 2024  1024 1024 1028 1079
#EndSection

Section "Monitor"
	Identifier   "A102GT"
	VendorName   "Idek Iiyama"
	ModelName    "Iiyama A102GT, VisionMasterPro 502"
	HorizSync    27.0 - 110.0
	VertRefresh  50.0 - 160.0
	Option	 "DPMS"
EndSection


Section "Device"
    Identifier     "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Monitor        "A102GT"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection    "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

My monitor specs:

Iiyama Vision Master Pro 502 (A102GT)

Sync Frequency
Horizontal: 27.0 - 110kHz
Vertical: 50 - 160Hz

Video Bandwidth : 240Mhz dot clock

---

### Post by Yfrwlf on 2006-12-18
One point about trying to use the "nv" drivers, it appears you weren't actually successful in trying to do that.  I'm not completely sure how it works yet myself, but I read you should be able to simply change "nvidia" in the driver section to "nv", restart X, and it should be using the nv driver instead.  If you run into a problem doing so, then what to do is beyond my knowledge, but of course a reinstall would get it back to using "nv" properly since it's what you were using before you installed nvidia.  You obviously shouldn't have to do that, and I don't know if switching back to nv will give you any better results.

Just to mess around with stuff I installed Kubuntu last night because I was having a problem with the resolution settings thingy in Gnome telling me I was at a refresh rate of 50 when I clearly wasn't.  As it turns out, the screen resolution program in KDE after I installed Kubuntu did display the correct refresh rate, unlike the Gnome one.  It also gave me many, many more resolution options to choose from initially.  I could select 1600x1200 @ 75 Hz, and if I moved it down to any lower resolutions then 85 Hz became available.  I note this because I'm just trying to figure out how it all works too.  I then installed the nvidia driver, and after that, interestingly enough, it removed all of the extra resolutions I could select except for all the ones that were defined in xorg.conf.  So, this suggests that maybe it's just the screen resolution settings program in Gnome that is screwed up and not reading the xorg.conf file correctly, or maybe not reading it at all!  If so, what is it reading?  I DON'T KNOOOOOOWWWWWWW!  Ahem.  The disfunctionality doesn't end there though, oh no!  The Kubuntu program, even though it would show all those things, if I selected something else and clicked "apply" it wouldn't actually change the resolution to what I set!  Both the resolution and refresh rate changes were not taking hold after clicking apply.  I'm going to mess around with it more in a bit to see if it was just a simple bug, I mean, maybe I need to manually restart X after selecting the new settings before it actually will change it for me.  If it is a problem with Gnome's Screen Resolution program, maybe you should install KDE and try that out instead.  You can just look up "Kubuntu" in the Synaptic Manager and install it that way.  I think when you install the kubuntu-desktop it pretty much installs the exact same stuff that you'd get if you did a fresh Kubuntu install except for perhaps a few additional programs.  I noticed, for instance, that Kubuntu uses Adept instead of Synaptic for it's package manager, but I think both programs are installable through the repositories.

So you are able to get 1024x768 @ 75Hz?  That's a lot better than 50 Hz.  At least that is SOME improvement, which is good.  Maybe the limiting factor for you is the drivers now, but I don't know.

The other thing I wanted to mention (and I know all this stuff is mostly pointless but I thought I'd just pass anything along that I could to try to figure out what's wrong and what solutions are out there) was that I was wondering to myself a short time ago if there was a way, other than submitting a bug, to tell the developers what works and what doesn't.  Well, after installing Kubuntu (from the actual Kubuntu image, not from the manager) I ran into my answer.  There's an app (forget what it's called, I will look at it again in a moment) that does JUST THAT.  I didn't go all the way through it, but it says it will run some tests on your monitor and other hardware, and you tell it if the device is working right and such, and then it will send all that information about your hardware and such to the developers so they can know about it.  That sounds like it may certainly be a good way to let the developers know the trouble you've had with your model of monitor and/or graphics card so they can possibly address that issue with a system update and/or in the next version of Ubuntu, 7.04.

I still think you might want to try the```
sudo dpkg-reconfigure xserver-xorg
``` thing, too, as another thing to try.  Back up your xorg.conf file first though before running it, and also I read that you should stop your xorg session before running it too, but that may just be needed on the older Ubuntu versions and not on 6.10.  To do it, hit alt-ctrl-F1, log in, and do a ```
sudo /etc/init.d/gdm stop
``` then run that dpkg-reconfigure line, then after you're done do a ```
sudo /etc/init.d/gdm start
``` and hopefully that might do *something*.

If none of this stuff helps, you might want to try saving your xorg.conf with your functional settings that give you 75 Hz at least and then maybe just reinstall? =P  Or try Kubuntu?  Then last but not least try Fedora until this issue gets resolved? =/  Or stick with Ubuntu at 75 Hz, which isn't thaaaaaat bad, but the desktop is a bit too small for my tastes at that res.  At least you have multiple desktops though! ^^

---

### Post by Caracal on 2006-12-18
oooooooooooooook right i just did what you said, shut down GDE, then followed the xorg-reconfigure menus (nothing was autodetected any differently), then i started GDE again.

It's now at 1280x1024@60Hz (my eyes! :'()

This is how my xorg.conf looks as a result (sorry for the spam!)
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"UK"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia GeForce 3 Ti200"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Iiyama"
	Option		"DPMS"
	HorizSync	27-110
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia GeForce 3 Ti200"
	Monitor		"Iiyama"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
And these are the (seemingly random) resolutions & refresh rates that are available to me:

640x480 - 53Hz / 70Hz / 71Hz / 72Hz
832x624 - 62Hz
960x600 - 60Hz
800x600 - 52Hz / 63Hz / 64Hz / 65Hz / 66Hz
1152x864 - 57Hz
1024x768 - 51Hz / 58Hz / 59Hz
1280x768 - 56Hz
1280x800 - 55Hz
1280x1024 - 50Hz

I think im going to do a bit more poking around, because obviously it's all TOTALLY wrong now lol >.< but hmm... yeah... i don't really know what to do now! :-k

UPDATE: Oh and if i go back into Applications > System Tools > NVIDIA X Server Settings, i can use a lot more resolutions and refresh rates that aren't listed in the system 'screen resolution' screen (so i'm able to at least go back to 1024x768 @ 75Hz now.

UPDATE2: If i change the driver to "nv" then reload X, it says it can't find a screen, so i have to revert back to my backup config :/

---

### Post by Caracal on 2006-12-18
Ohhh and i just randomly got kicked out of X, with this error!

(Couldn't be bothered to type it all out, so i just took a photo) :p

---

### Post by Yfrwlf on 2006-12-18
I want to know why reverting back to nv doesn't work.  If you don't uninstall anything when you install the nvidia drivers, you should still be able to switch back to nv from my newb understanding, so that is puzzling.  How about putting in your Live CD, and that way it will load the nv driver up *right*, and then editing the xorg.conf in that and giving it the refresh rate settings and the manual resolution @ hz lines in the screen section and stuff, and then restarting X on the Live CD and seeing if that works.  If you do ever need to know the user name or password, if it ever asks, google or so a search on the Ubuntu site for that info.  I dunno, just a thought.

Sorry about the long-winded replies =D

The program I mentioned for sending hardware specs is called the Ubuntu Device Database.  You could try it and see what it does, probably is just for feedback though, but it did say it would run some tests so *shrug*  It's really good to see them doing that though, that was exactly what I thought should be done and it will hopefully really help them to make sure that 7.04 has extensive hardware support.

Since it's been a while and no one with more knowledge than me has really replied much, and since you've tried lotsa stuff, I'd say try installing Kubuntu from Ubuntu repositories and see if KDE gives you any settings that Gnome won't.  I'm running Kubuntu from the ISO (wiped out my Ubuntu install, I just like trying new things, what can I say) actual Kubuntu OS and the monitor settings thingy is working fine now, I don't know why it wasn't doing anything before, weird.  Any way, maybe it will show you more options than Gnome will, because Gnome wouldn't show anything above 50 and Kubuntu shows 75 and 85 Hz and stuff as well as several options.

So, if you install Kubuntu through the repositories, and it doesn't work, maybe you should just try installing Kubuntu from ISO, and if that doesn't work, I think it's Fedora or some other distro time. :)

---

### Post by Yfrwlf on 2006-12-18
Until you get an answer about this, or until they get hardware support for your monitor, or until you get a new monitor. =D

---

### Post by Yfrwlf on 2006-12-18
BTW, it's also a good way to see if you like KDE or Gnome better.  KDE does have more options in general.  Some users find they like additional options, while some prefer the fewer "selected" options of Gnome.  Just depends on your taste. :)

---

### Post by Caracal on 2006-12-19
Hmmmmmmm i'd rather try and get this fixed instead of moving onto another distro :P

Is there any pros here that would be able to walk me though something we've maybe missed? :-k 

Hell, i'll let someone remotely access my damn PC if that's easier lol :P

---

### Post by Yfrwlf on 2006-12-19
Might try chat rooms too for live help.

---

### Post by Caracal on 2006-12-19
OK i just spent some time talking to ThePub on the ubuntu IRC channel, who suggested making these changes to my config:
```
Section "Monitor"

    Identifier     "Iiyama"

    HorizSync       28.0 - 91.72

    VertRefresh     43.0 - 85.0

    Modeline "1280x1024" 185.64  1280 1376 1600 2024  1024 1024 1028 1079

EndSection



Section "Device"

    Identifier     "NVIDIA Corporation NV20 [GeForce3 Ti 200]"

    Driver         "nvidia"

EndSection



Section "Screen"

    Identifier     "Default Screen"

    Device         "NVIDIA Corporation NV20 [GeForce3 Ti 200]"

    Monitor        "Iiyama"

    DefaultDepth    24

    SubSection    "Display"

        Depth       24

        Modes      "1280x1024"

    EndSubSection

EndSection



Section "Extensions"

    Option         "Composite" "Enable"

EndSection


```

and I STILL can't select 85Hz anywhere. In fact, the resolution/refresh rate options haven't changed at all since I made these changes (in both the 'screen resolution' screen, and the 'nvidia X server settings' screen! What the hell is going on!!!!!!!!!!

UPDATE: Just had a look at my Xorg.0.log, there doesn't seem to be any errors relating to the nvidia drivers etc, but it does set the resolution at the very bottom... i'm not sure where it's getting that from?!
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux caracal-desktop 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 19 22:04:23 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Iiyama"
(**) |   |-->Device "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0305 card 1043,8033 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8305 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1106,0686 card 1043,8033 rev 22 class 06,01,00 hdr 80
(II) PCI: 00:04:1: chip 1106,0571 card 0000,0000 rev 10 class 01,01,8a hdr 00
(II) PCI: 00:04:2: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:04:3: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:04:4: chip 1106,3057 card 1043,8033 rev 30 class 06,80,00 hdr 00
(II) PCI: 00:09:0: chip 1102,0002 card 1102,8040 rev 05 class 04,01,00 hdr 80
(II) PCI: 00:09:1: chip 1102,7002 card 1102,0020 rev 05 class 09,80,00 hdr 80
(II) PCI: 00:0a:0: chip 1033,0035 card 3083,0035 rev 41 class 0c,03,10 hdr 80
(II) PCI: 00:0a:1: chip 1033,0035 card 3083,0035 rev 41 class 0c,03,10 hdr 00
(II) PCI: 00:0a:2: chip 1033,00e0 card 3083,00e0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:0d:0: chip 10b7,7646 card 10b7,7646 rev 30 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 105a,0d30 card 105a,4d33 rev 02 class 01,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0201 card 107d,2861 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xde000000 - 0xdf5fffff (0x1600000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdf700000 - 0xe3ffffff (0x4900000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:4:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xde000000/24, 0xe0000000/26, 0xdf800000/19, BIOS @ 0xdf7f0000/16
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe4000000 from 0xe7ffffff to 0xe3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x30020000 - 0x3002ffff (0x10000) MX[B]
	[1] -1	0	0xdb800000 - 0xdb81ffff (0x20000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc00007f (0x80) MX[B]
	[3] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[4] -1	0	0xdd000000 - 0xdd000fff (0x1000) MX[B]
	[5] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[6] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[7] -1	0	0xdf7f0000 - 0xdf7fffff (0x10000) MX[B](B)
	[8] -1	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[12] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[13] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[14] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[15] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x30020000 - 0x3002ffff (0x10000) MX[B]
	[1] -1	0	0xdb800000 - 0xdb81ffff (0x20000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc00007f (0x80) MX[B]
	[3] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[4] -1	0	0xdd000000 - 0xdd000fff (0x1000) MX[B]
	[5] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[6] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[7] -1	0	0xdf7f0000 - 0xdf7fffff (0x10000) MX[B](B)
	[8] -1	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[12] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[13] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[14] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[15] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[16] -1	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x30020000 - 0x3002ffff (0x10000) MX[B]
	[5] -1	0	0xdb800000 - 0xdb81ffff (0x20000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc00007f (0x80) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xdd000000 - 0xdd000fff (0x1000) MX[B]
	[9] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[10] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[11] -1	0	0xdf7f0000 - 0xdf7fffff (0x10000) MX[B](B)
	[12] -1	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[18] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[19] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[20] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[21] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x30020000 - 0x3002ffff (0x10000) MX[B]
	[5] -1	0	0xdb800000 - 0xdb81ffff (0x20000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc00007f (0x80) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xdd000000 - 0xdd000fff (0x1000) MX[B]
	[9] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[10] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[11] -1	0	0xdf7f0000 - 0xdf7fffff (0x10000) MX[B](B)
	[12] -1	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[18] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[19] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[20] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[21] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[22] -1	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x30020000 - 0x3002ffff (0x10000) MX[B]
	[5] -1	0	0xdb800000 - 0xdb81ffff (0x20000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc00007f (0x80) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xdd000000 - 0xdd000fff (0x1000) MX[B]
	[9] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[10] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[11] -1	0	0xdf7f0000 - 0xdf7fffff (0x10000) MX[B](B)
	[12] -1	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[21] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[22] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[23] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[24] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[25] -1	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[27] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce3 Ti 200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.20.00.18.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce3 Ti 200 at PCI:1:0:0:
(--) NVIDIA(0):     Iiyama (CRT-0)
(--) NVIDIA(0): Iiyama (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 89); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B]
	[1] 0	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x2fffffff (0x2ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0x30020000 - 0x3002ffff (0x10000) MX[B]
	[8] -1	0	0xdb800000 - 0xdb81ffff (0x20000) MX[B]
	[9] -1	0	0xdc000000 - 0xdc00007f (0x80) MX[B]
	[10] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[11] -1	0	0xdd000000 - 0xdd000fff (0x1000) MX[B]
	[12] -1	0	0xdd800000 - 0xdd800fff (0x1000) MX[B]
	[13] -1	0	0xe4000000 - 0xe3ffffff (0x0) MX[B]O
	[14] -1	0	0xdf7f0000 - 0xdf7fffff (0x10000) MX[B](B)
	[15] -1	0	0xdf800000 - 0xdf87ffff (0x80000) MX[B](B)
	[16] -1	0	0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00008000 - 0x0000803f (0x40) IX[B]
	[24] -1	0	0x00008400 - 0x00008403 (0x4) IX[B]
	[25] -1	0	0x00008800 - 0x00008807 (0x8) IX[B]
	[26] -1	0	0x00009000 - 0x00009003 (0x4) IX[B]
	[27] -1	0	0x00009400 - 0x00009407 (0x8) IX[B]
	[28] -1	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[31] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(II) NVIDIA(0): Setting mode "CRT-0:1024x768_75@1024x768+0+0"

```

It wouldn't have anything to do with this part of my xorg.conf would it: ?
```
Section "Extensions"

    Option         "Composite" "Enable"

EndSection
```

Sloooooooowly going insane now!

---

### Post by Yfrwlf on 2006-12-20
If you want to go back to the nv driver:

I found out when you install the nvidia drivers it moves the xorg.conf somewhere else and makes it's own xorg.conf.  If you take that conf file and change the driver back to nv, it won't boot properly, because the nvidia stuff makes additional changes to it as well.  You could do a```
sudo updatedb
```and then```
locate xorg.conf
```and see if you can find the origional xorg.conf file so that you can go back to nv.  Reinstalling is another option to go back to nv.  If you want to then make some additional specifications in the origional nv xorg.conf file about your monitor, maybe you'll get more resolution and refresh rate options.  If you do, at that time you can only change the driver line to nvidia so you'll have hardware accelloration.  Just an idea! =D

Detection for your monitor/card configuration may just be poop though, and you've pretty much tried everything, so I'd try maybe Kubuntu and then try some other distro. :)

---

### Post by linux4me on 2006-12-27
I was having the same problem you describe with a new monitor, and trying the steps in the wiki didn't solve the problem, but the method described in this post, which varies a bit in generating the modeline and setting up the screen section of xorg.conf did the trick for me:

[http://www.ubuntuforums.org/showthread.php?t=321588&highlight=refresh+rate]("http://www.ubuntuforums.org/showthread.php?t=321588&highlight=refresh+rate")

You might give it a try and see if it works for you, too.

---

### Post by Kazna on 2006-12-29
@ OP: I know a method to solve your problem but you'll need a Windoze installation  to run it once... **do you have one?**

(as long as you have the correct drivers working)

Its easy and it should work, as nothing worked for me but this and its accurate.

---

### Post by jaja23bd on 2007-04-24
> **Kazna said:**
> @ OP: I know a method to solve your problem but you'll need a Windoze installation  to run it once... **do you have one?**
Its easy and it should work, as nothing worked for me but this and its accurate.


care to elaborate mate?

---

