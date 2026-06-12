---
title: "Clueless - Need to Change Monitor Identifier, Fix Resolution, More?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-01-12
I know next to nothing about using Terminal, so I'll need to know every single last detail of what I would need to type there (copy/paste has been my friend thus far) if I am needing to get into that, and I am quite sure that I am. 

I am running 6.06 LTS on an emachine that was saved from being junked.  I installed an old 30GB HD and the install went brainlessly easy.  I was running a 17" CRT at 1280x1024.  However, sitting on the floor with monitor and keyboard became too much of a pain. 

Today, I received and hooked up an IOGear GCS62 in order to control both of my computers, the other being XP, and view it all from my 24" LCD (Gateway FPD2485W) which I run at 1920x1200.  

My problem showed itself when I switched to the Ubuntu machine and was presented with 800x600, I believe it was, with no option to change anything.  I found this link: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) and followed the instructions under Run the Autodetect Script Again.

I clicked 'Enter' through all sorts of things I mostly did not understand and it DID bring improvement, but only to the tune of 1280. It also seems a bit fuzzy, but I'm not sure if that's the resolution messing with me or what.  

Anyhow, I went to the next step to see what would happen, under "Undetected Monitor Specs."  I found:

Section "Monitor"
        Identifier      "NEC FE700+"
        Option          "DPMS"
EndSection

The NEC is what I had plugged in when I installed Ubuntu.  

A little further down, I get:

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset In$        Monitor         "NEC FE700+"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "64$




I have searched through various threads here that seem to have similar themes, but haven't found answers that I can understand, or that necessarily address my specific situation.  I could be totally blind at this point, though. ](*,) 

As for a video card, the hardware rundown sticker on the emachine says "Intel Extreme Graphics 3D"  

So, apparently I need to get this thing to recognize the monitor I have now, change the identifier somehow?  And then add the HorizSync and VertRefresh annnnnd get it to give me more/better/bigger resolution choices?  

As an aside to the monitor/KVM/resolution problem, it seems the left side of the screen is cut off with quite a bit of extra space available on the right.  I haven't adjusted anything with the monitor since I am unsure as to how this will be resolved, if it can be resolved, and the fact that the monitor is perfect with my other machine. 

Please help.  I really want to try Linux, I really want to try Ubuntu, and I really want to learn.  It's just that much of the tech help I've seen starts with instructions a few steps after where I'd need them to be.  It's getting to be a bit late for me and I'm very tired, I hope I've made some sense. 

Thank you in advance.

---

### Post by olejorgen on 2007-01-12
I'm by no means an expert, but you might try to run ```
sudo dpkg-reconfigure -phigh xserver-xorg

``` with your new monitor connected. This will reconfigure your xorg.conf. If that doesn't work, you could try to manually add 1920x1200 to Modes in xorg.conf. (I'm not sure if this might harm your monitor, so maybe you should wait for more replies before you do that :))

Sorry if I'm talking over your head

---

### Post by Wartooth on 2007-01-12
No, not at all, that was great!  In fact, I ran that and I am now, at least at 1600x1200.  

I checked out xorg.conf and found that it does at least know which monitor I have, although it's not listing up to 1920 yet. It also does not list the Horiz and Vert, which it apparently should according to that one HowTo link. 

One problem has come up now, though...I switched back to XP, and now IT is messed up!   That doesn't make any sense, I'd think, for me to run something on the Ubuntu box and have it alter the XP one?!?! The XP box is at 1600 and is very fuzzy.  

So, I will try editing the xorg.conf file according to that HowTo link and will return with results. 

Thank you for answering, progress is now seen on one front at least, if not trouble on another.  Haha!

On Edit:  Rebooted XP and it's back to normal there.  Wild.

---

### Post by Wartooth on 2007-01-12
Unfortunately, going in and adding 1920x1200 to the Screen Modes area didn't give me an option of 1920 in the drop-down menu.  I added my Horiz and Vert, but no real noticeable change there.  

I think I've run out of things I am willing or able to try without further advice and insight.  

But, hey, it's twice as good as what it was when I started!

---

### Post by Ocxic on 2007-01-12
after you change your xorg.conf you have to restart X or they won't go into effect.

either ctrl-alt-backspace
or 
hit alt-f1, login and type "sudo /etc/init.d/gdm restart"

---

### Post by olejorgen on 2007-01-12
hm.. that's really strange oO but if it's back to normal it's not that scary I guess

Anyway, as Ocxic said, you need to restart X to get to new options

---

### Post by Wartooth on 2007-01-12
I've restarted X, to no avail.  Even used both methods mentioned...just...in...case.  Still limits me to 1600.  :\

I do appreciate the replies, though!

---

### Post by Wartooth on 2007-01-12
I've poked around enough to find that I have The Intel 82845G, on board, of course. 

Going out on a limb here, is there any possibility installing this would help? [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)
If so, I'd need to know where to untar it to, as that's something that has eluded me so far in these past few days of Ubuntu-ing.  

I'm finding some things that give me hope that widescreen can be done with this chipset, other things that make it seem like it is a flat-out impossibility.

---

### Post by Ocxic on 2007-01-13
it's possible that that is your max resolution also, uless you know otherwise.

---

### Post by Wartooth on 2007-01-14
I'm sort of fearing that, though I have seen what appears to be conflicting things.  I'm wondering if the driver download would be of any benefit. As far as I can tell, it will do higher resolution, but it does not do widescreen as-is. Although, after a while, reading all the various specs and such on this chipset and others, things start to just mush together in my brain.

---

### Post by blackened on 2007-01-14
Have you generated the proper modeline for your monitor yet? To do this in terminal type:```
gtf 1920 1200 60
```

It should output something in this format (but with your info)
```
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
```

Copy from where it says "Modeline" to the end of the line and then paste it into your /etc/X11/xorg.conf file's Monitor section as so:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	60-75
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R100 QD [Radeon 7200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900_60.00" "1280x960" "1440x900" "1152x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Also note that you need to alter the first entry of the "Screen" section's "Mode" entry to show what the first part of the modeline says.

---

### Post by Wartooth on 2007-01-14
No, I hadn't done that, and I thank you for mentioning it.  I followed your instructions, and re-started X, but still no change in options.  I'm thinking that perhaps this chipset can't do widescreen, unless that driver update contains something to make it widescreen-friendly.

---

### Post by blackened on 2007-01-14
My only other possible suggestion would be this:

Swap the video cards in your machines, and go through all the steps suggested here again.
Foremost I would suggest trying the card you're having trouble with under Windows and see if it can do widescreen there. If it can, then I'd just leave it there and try your hand at getting the widescreen working with the other card.

I don't know if this is even possible considering they may be two different types of cards, but it's worth a shot if it's possible.

---

### Post by Wartooth on 2007-01-16
Howdy, 

As far as I know, this is on-board video and can't be swapped out?  I could be wrong, but that's what I read about these emachine t2984s.  The only thing I did when the case was open was to throw in the old 30GB HDD in.  

I also can't try it under WIndows as this isn't a dual-boot. Only thing on here is Ubuntu. :)

The joys of a beater-box, I guess.

---

### Post by blackened on 2007-01-17
Have you tried this method yet: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28Intel.29]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28Intel.29")
Also note the *Enabling Large Widescreen Support* section for this card just below it.

---

### Post by Wartooth on 2007-01-17
Ahh, I have not installed the graphics driver, although I have tried the bit about enabling widescreen, or something quite close to it.  It appears from the graphics driver area that I need to install Alien?  

I will attempt to install Alien (let's hope I get this right), follow those commands, and report back. 

I'm glad you've let me know that I haven't run out of things to try yet :)

---

### Post by Wartooth on 2007-01-17
Well, I hope I did this right, but there appears to be no change.

I installed Alien.

I downloaded the driver. 

It spewed forth this:

xyz@box:~$ sudo alien dri-I915-v1.1-20041217.i386.rpm
Warning: Skipping conversion of scripts in package dri-I915: postinst prerm
Warning: Use the --scripts parameter to include the scripts.
dri-i915_v1.1-20041218_i386.deb generated
xyz@box:~$ sudo dpkg -i dri-i915_v1.1-20041218_i386.deb
Selecting previously deselected package dri-i915.
(Reading database ... 73705 files and directories currently installed.)
Unpacking dri-i915 (from dri-i915_v1.1-20041218_i386.deb) ...
Setting up dri-i915 (v1.1-20041218) ...

I didn't know what to think of the "Warnings".

I edited the xorg.conf again according to the widescreen blurb.  Restarted X. 

Checked my options, and 1600 is still my max. 

Did I do something improperly, or is this basically the end of the road of things to attempt?

---

### Post by blackened on 2007-01-17
Did you also try the suggestion for 915resolution?

---

### Post by Wartooth on 2007-01-17
I just ran 915 resolution...this is what it told me:

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3kB of archives.
After unpacking 127kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe 915resolution 0.5-1ubuntu6 [14.3kB]
Fetched 14.3kB in 0s (18.3kB/s)
Selecting previously deselected package 915resolution.
(Reading database ... 73710 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5-1ubuntu6_i386.deb) ...
Setting up 915resolution (0.5-1ubuntu6) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution or install 'vbetool'.
invoke-rc.d: initscript 915resolution, action "start" failed.

Um...hm.  It appears that something is not as it should be.

Opening this in nano and seeing what I can see to do what I can do.

---

### Post by Wartooth on 2007-01-17
Well, when running 915resolution, I get my list, but the list goes from 1600x1200 to 1920x1440.  So, I assume that this means that widescreen is, in fact, a no-go. OR, does the above mean I have to manually enter 1920x1200 into one of the above options and sort of force my way through it?  Somehow I don't see that working.

---

### Post by Wartooth on 2007-01-17
I've gone through all of that editing and such of 915res and xorg and rebooting and all.  No change.  Even attempted auto settings in 915resolution, but when i run 915resolution -l, I don't see any 1920x1200 options.  What's funny is that I DO see 1920x1440, yet that isn't given to me as an option in my drop-down. 

Mode 30 : 640x480, 8 bits/pixel
Mode 31 : 640x400, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 40 : 640x480, 15 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 42 : 800x600, 15 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 44 : 1024x768, 15 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 48 : 1280x1024, 15 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4a : 1600x1200, 15 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4c : 1920x1440, 15 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel


Is "Depth" the same as the bits/pixel thing, essentially?

What I'm getting at is...the DefaultDepth in xorg is 24, yet that's not even an option in bits/pixel, yet 8,15 &16 are.  So what if I were to change the DefaultDepth to, say, 16, edit the Modes to reflect 1920x1200 and restart X?  Or am I grasping at straws?

I've replied to my own thread far too many times in a row.  Sorry.  It seems as though I keep having thoughts AFTER posting.  :/

---

### Post by blackened on 2007-01-17
Ok, so apparently you have the driver installed. From here I would proceed this way:
Do exactly what's listed at [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_Correct_the_Graphics_Resolution_.28Intel.29]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_Correct_the_Graphics_Resolution_.28Intel.29") first.
After that's done, then do the enabling widescreen support portion [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_enable_Large_Widescreen_Support]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_enable_Large_Widescreen_Support").
Make sure you check the modeline that they list in that section with your own gtf output for 1920x1200.

---

### Post by Wartooth on 2007-01-17
Just tried all of that...no change. :( 

I have to wonder why it is that I see all these other options in various areas in Terminal, but I have only 640x480, 800x600, 1024x768, 1280x1024 and 1600x1200 available in the drop-down menu.

---

### Post by blackened on 2007-01-17
The drop-down menu in the resolution changer program directly reflects the resolutions listed in your xorg.conf. I'm at a loss as to other options short of you getting an add-on video card.

---

### Post by Wartooth on 2007-01-18
Yep, I think this is the end of the line with this.  I do thank you for helping so much.  I guess I'm going to have to decide what I want to do.  

I feel bad having this big monitor and not using it properly (Christmas gift from my husband) so much of the time.  As time passes, I am using Ubuntu more and more and all but ignoring XP. However, I think I'd want to myself a little longer-term stick-to-it-ness before switching machines, buying parts, or building one, etc. I very much like having the switch and having both going at the same time.  Hmmm.  Decisions, decisions.

---

