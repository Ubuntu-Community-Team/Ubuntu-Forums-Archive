---
title: "Change screen resolution in 9.04"
date: 2009-05-08
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-08
Much to my surprise, I managed to get Ubuntu 9.04 working on an old Mac G4. The only thing wrong so far is that I can't figure out how to change the screen resolution, which is currently at 800x600. The System>Preferences>Display app doesn't give me any options but 800x600 and 640x480 even though the monitor is happy at higher resolutions. My monitor is a Sony Multiscan 17sfII which runs 1024x780 @ 75hz on the same Mac with no trouble. I tried an earlier version of Kubuntu (6.10) which had a bunch of monitor profiles with it and I was hoping this distro did too, but if it does I can't find them.

Isn't there a prefs file somewhere I can edit to deal with this cramped display? Sorry if this is newbie stuff, but really, in linux terms, that's what I am.

---

### Post by stream303 on 2009-05-09
You'll need to manually edit your /etc/X11/xorg.conf file.

First, make a backup of the original:

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
```

(note the Capital X)

From a terminal, you can edit the original with root priveleges:

```
gksudo gedit /etc/X11/xorg.conf
```

There might be next to nothing inside, but don't worry.

The specs for your monitor were found, and I suggest adding these lines to your xorg.conf:

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
             EndSubSection
EndSection
```

Be mindful of what lines need start and end-quotes, and those line that don't need quotes.

Save the file, quit the editor, and then use the logout function to restart X.  Or you could just restart the computer.  There are other ways to do this, but as a start, this is easiest.

Let us know how it goes!

---

### Post by Benboom on 2009-05-09
THANK YOU SO MUCH.

I'm copying this onto my main Mac so I can do this when I reboot the Ubuntu system later this morning. I read a little on this and as a result I was so afraid of messing with the xorg.conf file that I ALREADY backed it up! :)

Very helpful; thank you again.

UPDATE: I got it working, thanks to your help! I first simply added the monitor but didn't realize I needed to comment out the duplictaed portions of the original. When I did that and rebooted I got the high resolution screen. And now I also see a bunch of other resolutions supported, too.

This is just great.

Thanks again!

---

### Post by Benboom on 2009-05-09
Issue solved!

---

### Post by Benboom on 2009-05-09
Issue solved! Typing this on large screen!

---

### Post by stream303 on 2009-05-09
Wow - that usually doesn't happen.  I thought for sure that this was just an exercise to something larger.  I'm glad it worked right off the bat.

Which machine do you have?
[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

Also, normally I just check to make sure that System > Preferences > Appearances > Fonts > Subpixel smoothing is checked for lcd's and In the details tab I run "slight" hinting.

---

### Post by Benboom on 2009-05-09
It's a [G4 450]("http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_450.html")

So far I'm not having any problems with the way it's displaying things but I will look at the smoothing to see if it makes a positive difference.

In fact, now that I have a screen that functions properly the only thing I have found that I'm not quite happy with is that the audio output from the machine when running Ubuntu is considerably less than it is under OS X. I think I'll post another thread about that; it's about 15 dB lower - that's a lot. On my Mackie mixer it's the difference between 10AM and 3PM on the input level knob.

But since the main reason I was doing this was so I could see if I could get a handle on Ubuntu prior to our purchase of a netbook for my wife the audio issue is pretty secondary; I just enjoy using the OS and I'm a little surprised because my past experience with Ubuntu (5.10) was not great. I would rather run Ubuntu than Windows but she's used to Windows and I thought that for the net surfing and word processing she's likely to do Ubuntu would be okay. Now that it looks like a "real" computer I'll let her play around with Open Office and Firefox on it.

---

### Post by stream303 on 2009-05-10
Ah, a Sawtooth!  Hang on to that baby for sure!

I mentioned a fix for your audio in the other thread - see if that works.

In the meantime, could you do us a favor and post your full /etc/X11/xorg.conf file here?  I'm really interested since it appears your machine is running an ATI Rage card, and not an nvidia card - unless you swapped it out...

This will help confirm it:

```
lspci | grep VGA
```

(All-caps on VGA)

What would really be cool in addition to your xorg.conf file, would be the output of your **/var/log/Xorg.0.log** for the record.  It will be a bit long, but will help out greatly.
(again, make Xorg.0.log start with a capital X)

Man - a Sawtooth - wish I had one.

---

### Post by Benboom on 2009-05-10
Wow, two for two! The Line Out level was all the way at the bottom in alsamixer and I raised it to 100 and compared it with my second Sawtooth running Audion with the same song and now the volume levels for both machines appear to be the same; this is great. I wasn't even aware of the existance of alsamixer.

As to the rest of your comments, here goes. I'll post the xorg.conf file but I can't figure out how to make the formatting look correct like yours does. Mine IS formatted like yours is but when I post it the formatting just disappears. With that in mind, here goes [entire file, including comments]:

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

#Section "Monitor"
#	Identifier	"Configured Monitor"
#EndSection

#Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
                SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
                EndSubSection
EndSection

---------------

As for the graphics card, you are right. The machine has the original card and this is the result of the command you listed:

0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

----------------

I'm curious as to why you seem to like the Sawtooth. Most people I have read generally dismiss them.

*I* like these old Sawtooth machines, although the 128 gig limit on the hard drives is a PITA. I got around that with the intech high cap driver and my main one (1ghz Sonnet processor) has a terabyte of storage. But the Ubuntu machine has only a couple of 120 meg drives in it and even if I added bigger ones with the intech driver Ubunu would not recognize the extra space. :-( They are also easy to upgrade and have tons of space inside. I think the fact that I have two ten year old computers which are still able to function in today's world is a reasonable testament. I must say that this old G4 with the 450 mhz processor under Ubuntu, while sort of slow, is also pretty nice now that you have sorted out my initial major issues.

Thanks so much! I'm sure I will have other questions as I continue to explore it.

---

### Post by stream303 on 2009-05-10
Thank you so much posting those files - it really helps!

As to the 128gb issue - this is similar to the problem faced with early G3 iMac owners that have 8gb partitioning limitations when they find out that they have upgraded their drives.

The solution is that the **root** partition must not extend beyond these boundaries, and typically one has to use manual partitioning (rather than letting guided partitioning just "use the whole disk")

What I describe here is for a dedicated install, and not any sort of dual-boot!

The Linux ppc installers have no way of knowing about these root boundaries on these specific boxes that have these limitations.

Essentially, one keeps that root partition well below the boundary to be safe - that is in your case make sure that root is no larger than say 120 gb, and the rest of the partitions like /home are beyond it is ok.

The problem is that we need special apple partitions before root, and unless you know how to do it, it can be a pain.

One solution if starting from a bare disk is to purposely fail with guided partitioning "using the whole disk".  Go ahead and install this way - the special apple partitions will be written, although /root is too large and the system will not come up.

Now, reinstall again, but this time, do a MANUAL partition and leave those first two special apple partitions alone!  Manually create or resize a /root that is under 120gb (or say 7gb for G3 iMac users), and a swap about 1x or 2x your ram.  Now your whole disk is in use because it is partitioned correctly for that root limitation.

(swap size is a whole 'nother issue that you can check out elsewhere)

In the former ubuntu installers, you could do this all in one shot using the "BACK" technique, as I call it.  You could start out with guided partitioning "using the whole disk", then BACK out and resize the root partition and add a swap.  Unfortunately, you cannot do that these days, so here is the somewhat bodged-together version where you reinstall twice. :)

This is an attempt to explain how to do it if you don't have much knowledge of the special apple partitions and manual partitioning skills.  Experts can explain it much better than I for sure. :)

But in the end, you can get around those 8 and 128gb root partition limitations and put the rest of the disk to good use!

---

### Post by BlutBoomer on 2009-09-04
Hi I am really not sure what monitor I've got, its a tube by an unknown make and model, My screen res was fine before at 1024x768 but today it suddenly changed to 800x600... I really don't know how to access the thing that everybody is mentioning, can someone please tell me how?

---

### Post by s12en7s120 on 2009-09-13
you know I noticed that you guys had just added the script? I completely erased my old and put in the new one, then went to system>preferences>display and was able to change my resolution to the appropriate setting. That was pretty great. it worked just as good.

---

### Post by s12en7s120 on 2009-09-13
[SIZE=4]Go to Applications on your top left of the screen, then click on Accessories. After that click on Terminal. That will open your command, then type this (EXACT!). [/SIZE]gksudo gedit /etc/X11/xorg.conf[SIZE=4]  this is case sensitive. That is how you get into the thing that will let you edit your video driver config.
[/SIZE]

---

### Post by s12en7s120 on 2009-09-13
[SIZE=4]Than you copy this from here. 

[/SIZE]Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       31-65
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
             EndSubSection
EndSection
[SIZE=4]
[/SIZE][SIZE=4]Then you need to copy your original setting to notepad or something and save it so if your screen messes up good than you can go back and put in your old code.  After you pasted the new code into your editor, click "save" and exit. Reboot or Re-log back in and you will notice your screen will glitch a little, so then go to System>Preferences>Display and change your screen resolution to the proper size. I had to change mine to 1152x864[/SIZE]  [SIZE=4]and now it works perfect, no problems. It took me 3 different sizes to find the right one, but just going down does not mean your screen will get smaller, because the one above my setting now was tiny and only fit on half of my screen. [/SIZE]

---

### Post by s12en7s120 on 2009-09-13
that didn't copy right on here. That script you can get from page 1 and it should be on one of the first comments.

---

### Post by Cpyles07 on 2009-09-15
I was so close to pulling my hair out trying to set up my DLP TV And I couldnt get better than 640x480 and I knew the tv supported  alot higher resolution. Now I am enjoying 52 inches of DLP Ubuntu goodness. 

So happy I found this.

You guys rock.

---

### Post by FreeFelix on 2009-09-19
Hi I have tried this with my iMac 24" with an NVIDIA GeForce 8800 GS and max res of 1920X1200

Can't seem to get any extra res options showing in the display options.

Have tried a few - should any of the settings be different  eg depth be 32 for example?

any help be good

ta much

:)

---

### Post by saidbakr on 2010-02-23
Hello,

it succeeded with me to make the resolution 1024x768 to be an option of System->Prefrence->Display->resolution list.

However, the screen keep annoying blinking.

```

Section "Monitor"
        Identifier      "Configured Monitor"
       ** HorizSync       31-65
        VertRefresh     50-87
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1024x768"
             EndSubSection

```

Without using HorizSync values it blinks with annoying blinking, when I use HorizSync value the screen turns into mssy and I could not deal with it.

How could I fix this?

When  use smaller VertRefresh range 50-75 the 1024x768 resolution does not be available.

My Screen is TVM LR 4G 14" It was work at 1024x768 resolution on Windows

---

### Post by linuxopjemac on 2010-02-23
Follow [this thread]("http://ubuntuforums.org/showthread.php?t=1392023&highlight=resolution&page=2"). There are ways to get the right modelines for your monitor. You have to find them.

---

### Post by saidbakr on 2010-02-23
The following the output of gtf for Modeline : gtf 1024 768 60
```

"1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

```

Where could  able to place it in the code regarded above?

---

### Post by linuxopjemac on 2010-02-23
In the Monitor section, as in 

[http://mac.linux.be/content/setting-xorgconf-manually-xrandr](http://mac.linux.be/content/setting-xorgconf-manually-xrandr)

---

### Post by saidbakr on 2010-02-23
Wow! I got it!

First of all I used the first code regarded at the beginning of this topic. However, I got [my monitor specifications]("http://www.monitorworld.com/Monitors/tvm/as4glr4g.html") and I knew its H Freq and V Freq.

The final code is:
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       30-50
        VertRefresh     50-120

EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1024x768"
             EndSubSection
EndSection

```

However, Although another resolutions values appeared in the resolutions under display, prefrence, system , but the default refresh rate for 1024x768 is 87 Hz which leads two screen blinkng, but I found another value for the refresh rate to 60 Hz and then everything is gone fine.

---

### Post by Carlitoes on 2010-07-12
Hey thanks that worked for me i know have an acceptable resolution  just wondering though, Was that only for the g4 mac specs? I'm using a fujitsu siemens v5535 just seems to be a lil sluggish maybe its the refresh rate idk.  Thanks again i will have a little play around and see if it can be improved!

---

### Post by jimmibennett on 2011-01-19
Thank you Stream 303, I have had this problem for a year now, and after countless attempts to remedy the situation I gave up. Thanks to you however, my screen resolution is PERFECT.

THANK YOU VERY MUCH! :)

---

### Post by rocuan on 2012-01-29
Know it is bad form to bump an old thread but have to say thank you!

I modified my xorg.conf for an LG E2241 Flatron monitor on 10.10

```

Section "Monitor"
    Identifier    "LG E2241"
    HorizSync     30.0-83.0
    VertRefresh   56.0-75.0 
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "LG E2241"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1920x1080"
             EndSubSection
EndSection

```

---

### Post by coffeecat on 2012-01-29
> **rocuan said:**
> Know it is bad form to bump an old thread

Indeed! :)

The thread is an old one referring to a now-obsolete version of Ubuntu and has wandered around a bit. If anyone needs help changing their screen resolution in a supported version of Ubuntu, please start a new thread, linking back to this one if you wish.

Thread closed.

---

