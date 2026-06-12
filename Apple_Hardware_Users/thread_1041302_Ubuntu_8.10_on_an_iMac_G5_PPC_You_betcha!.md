---
title: "Ubuntu 8.10 on an iMac G5 PPC? You betcha!"
date: 2009-01-16
forum: Apple Hardware Users
---

### Post by inigomontoya on 2009-01-16
I just wanted to share with you all my success with getting a nice usable install of ubuntu 8.10 on a iMac G5. I think this section needs a bit more positivity. 

Interesting story, bear with me.  I acquired this machine at work.  Do I work in an office or computer store?  No, far from it.  I am a simple garbage man (sanitation engineer sounds better).  One of my customers had this stuffed in their garbage can.  I've obtained many usable machines amid piles of trash bags in my day but I've never come across an Apple machine as new as this.  Upon getting it home and scrounging for a power cable I plugged it in and it fired right up.  The screen turned on and then displayed a ? and halted.  Upon a little research I found out that this meant the OSX install was damaged or missing.  Turns out all that was wrong with this machine was a dead hard drive.  I just so happened to have a spare SATA drive I found (at work) and installed it.  I decided to try OSX Leopard.  Needless to say I found it a bit lacking.  Why else would I be posting this?

I have a few years experience with linux.  So, I set out to get a good os on this thing.  The hurdle of the PPC architecture severely limited my options.  I tried Fedora, SuSE, Yellow Dog, an older version of Ubuntu, but none of them had everything working correctly.  Wireless didn't work, graphical problems, bootup failures, kernel panics.  After reading the FAQs in this forum I got 8.10 installed just fine.  At first boot I noticed some peculiarity in the rendering of the desktop, but it was quickly fixed by compiling the latest xf86-video-ati driver from git.  Wireless was spotty but that was remedied by compiling the 2.6.28 kernel.  Now everything works desktop effects included, well except the 24-bit color problems some seem to be having.

I then did some modifying.  Installed wicd (much better than Network Manager IMHO), hyroxygen icons, and the dust theme.  Thanks to this forum and Linux for the wealth of information and shared experiences. I now have a fast, free (in more ways than one), usable desktop which is also pretty to look at.  

Here is the result:

---

### Post by Houli on 2009-01-16
Haha that's great mate. It's good that you've had a great experience with Ubuntu on a Mac. I however hadn't. Still can't get the bluetooth keyboard by Apple to work. Hopefully the kernel updates to support it.

-Houli

---

### Post by stream303 on 2009-01-16
That's great!

I have the earlier version (no als, no isight) with an nvidia card, and it appears you have the more recent ati-driven rev-b or rev-c.  Do you know which one you have?

Or more specifically, does yours have the built-in web-cam?

Also be sure to check the health of your motherboard capacitors - see if any of those little cylindrical parts have bulging tops or any signs of leakage just to be safe.

---

### Post by inigomontoya on 2009-01-16
> **stream303 said:**
> That's great!

I have the earlier version (no als, no isight) with an nvidia card, and it appears you have the more recent ati-driven rev-b or rev-c.  Do you know which one you have?

Or more specifically, does yours have the built-in web-cam?

Also be sure to check the health of your motherboard capacitors - see if any of those little cylindrical parts have bulging tops or any signs of leakage just to be safe.

This appears to be a revision B so no webcam.  I too read about the bad capacitors issue and it appears my board does not have them. They appear to be of a newer type. I was sure to check all of them last time I had it open.

---

### Post by stream303 on 2009-01-17
Ok, great - it will be interesting to see if the ALS (automatic light-sensor) works to automatically change the screen brightness, but I wouldn't be surprised if it doesnt work.

However, at least on mine, the backlight for the lcd *will* turn off if you change that preference in the powersave menu.

Couple of tips - the font dpi calculates out to be about 99 as a starting point before adjusting any font sizes, rather than the default of 96.  I use this calculation:

```
echo 'scale=2;sqrt(1680^2+1050^2)/20' | bc
```

And, doublecheck to see if your cpu is throttling speed if you don't want it running full-speed all the time.  (just pop a cpu-freq monitor in the top panel if you are on gnome).

If it isn't scaling, you can fix the powernowd script, or alternatively install cpudyn for less latency during the switch.  (It isn't in the index, but is about half-way through this faq: )

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

The iMacs make for sweet machines - I'm surprised that with the ati card, you didn't have to manually edit the /etc/X11/xorg.conf file.

Good times ahead!

---

### Post by inigomontoya on 2009-01-17
> **stream303 said:**
> Ok, great - it will be interesting to see if the ALS (automatic light-sensor) works to automatically change the screen brightness, but I wouldn't be surprised if it doesnt work.

However, at least on mine, the backlight for the lcd *will* turn off if you change that preference in the powersave menu.

Couple of tips - the font dpi calculates out to be about 99 as a starting point before adjusting any font sizes, rather than the default of 96.  I use this calculation:

```
echo 'scale=2;sqrt(1680^2+1050^2)/20' | bc
```

And, doublecheck to see if your cpu is throttling speed if you don't want it running full-speed all the time.  (just pop a cpu-freq monitor in the top panel if you are on gnome).

If it isn't scaling, you can fix the powernowd script, or alternatively install cpudyn for less latency during the switch.  (It isn't in the index, but is about half-way through this faq: )

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

The iMacs make for sweet machines - I'm surprised that with the ati card, you didn't have to manually edit the /etc/X11/xorg.conf file.

Good times ahead!

Oh yes, the ALS sensor.  I don't think it works, by shining light on it or covering it with my finger i see no change in LCD brightness.  Scaling is not an issue for me as I'd rather have as much performance as possible with 0 latency between switches.  I might just see if i can get it working for something to do :D

Oh and thanks for the font DPI tip.  I thought something looked a bit off on the font size.

I was surprised as well that I didn't have to edit the xorg.conf.  I did end up editing it to set some performance related options for xf86-video-ati.  That driver has improved by leaps and bounds over the last 6 months.

The only thing that is really bothering me is that the LCD displays 16bit colors when set to 24bit.  I know it has something to do with this screen only having 6 bits per pixel.  The frustrating thing is that the "Dac6Bit" option in xorg.conf does nothing.  I've played around with the source of xf86-video-ati and looked for a possible bug, but i'm afraid i'm not familiar enough with C.

---

### Post by McFrostey on 2009-01-17
well all I have to say is OMFG LUCKY lol I would soo kill for a iMac G5 even though the G4 is still awesome gratz... "i wish i was a garbage man"

---

### Post by g0bez on 2009-01-18
Would you be so kind as to post your install process? I'm trying to accomplish exactly the same thing that you are, on the same hardware.

Which iso did you use?
Any particular settings?

I like your theme/icons/etc... very nice setup!

---

### Post by g0bez on 2009-01-18
> **g0bez said:**
> Would you be so kind as to post your install process? I'm trying to accomplish exactly the same thing that you are, on the same hardware.

Which iso did you use?
Any particular settings?

I like your theme/icons/etc... very nice setup!


Actually... scratch that. I think the repository was down last night when i was trying to install and tonight it is working just fine. I've used ubuntu alot on non-PPC architecture... so I thought I knew what I was doing, but was going crazy when I couldn't get it to update!

Currently i installed via the server iso (i want several server features)... and used apt-get install ubuntu-desktop -y  ... 10 more minutes and I will hopefully be set!

Then it is time for the hardware config... should be interesting.

---

### Post by inigomontoya on 2009-01-18
> **g0bez said:**
> Actually... scratch that. I think the repository was down last night when i was trying to install and tonight it is working just fine. I've used ubuntu alot on non-PPC architecture... so I thought I knew what I was doing, but was going crazy when I couldn't get it to update!

Currently i installed via the server iso (i want several server features)... and used apt-get install ubuntu-desktop -y  ... 10 more minutes and I will hopefully be set!

Then it is time for the hardware config... should be interesting.

Be sure to let me know if any problems arise.  If you have them then I'm sure I had them at some point.

---

### Post by stream303 on 2009-01-18
> **inigomontoya said:**
> Scaling is not an issue for me as I'd rather have as much performance as possible with 0 latency between switches.

In that case, you'd want **cpudyn** as the frequency scaler, since it has very low latency between switches as compared to powernowd - even when you get powernowd working.  Just install cpudyn from the repos and see.  A couple of guys who do audio editing etc tried it and it works very well.  It saves about 10 watts of power when idle and shouldn't affect your operations.  Check it out.  Cpudyn is ideal for non-smp boxes, although it works to a fashion with multiple cpu's.

> The only thing that is really bothering me is that the LCD displays 16bit colors when set to 24bit.  I know it has something to do with this screen only having 6 bits per pixel.

I think you may be confusing color depth with hardware specs - in this case it is because our lower-cost flat panels really only have 6-bit hardware, as compared to the higher quality ones that do 8-bit - again nothing to do with color depth.  If you are running an nvidia card, you can force that option which is normally off  (from the nv man-page)

>  Option "FPDither" "boolean"
Many digital flat panels (particularly  ones  on  laptops)  have only  6  bits per component color resolution.  This option tells the driver to dither from 8 bits per component to 6  before  the flat panel truncates it.  Default: off.

I don't think this applies to super displays like the Apple Cinema displays with 8-bits, but for our iMacs, we are down in the 6-bit area.  And, I don't think the opensource ati driver can do this.  It does make a difference, even on my non-ppc boxes that have nvidia cards.  But this is a hardware spec, and not a color-depth issue.

Getting back to color-depth, it is strange that your machine doesn't seem to want to do 24-bit color depth.  How did you determine that?  Oh, one last check - does your screen-resolution gui show 1680x1050 at 60hz?

---

### Post by inigomontoya on 2009-01-18
> **stream303 said:**
> 


I think you may be confusing color depth with hardware specs - in this case it is because our lower-cost flat panels really only have 6-bit hardware, as compared to the higher quality ones that do 8-bit - again nothing to do with color depth.  If you are running an nvidia card, you can force that option which is normally off  (from the nv man-page)


I don't think this applies to super displays like the Apple Cinema displays with 8-bits, but for our iMacs, we are down in the 6-bit area.  And, I don't think the opensource ati driver can do this.  It does make a difference, even on my non-ppc boxes that have nvidia cards.  But this is a hardware spec, and not a color-depth issue.

Getting back to color-depth, it is strange that your machine doesn't seem to want to do 24-bit color depth.  How did you determine that?  Oh, one last check - does your screen-resolution gui show 1680x1050 at 60hz?

When set to use 24-bit color lots of color banding is apparent as if i'm running in 16-bit mode, that's what i mean.  It is running in 24-bit but it doesn't look that way. So is OSX dithering this before it's displayed?  I saw no color banding while running OSX.  I have a 17inch imac so the resolution is 1440x900.  It is correctly displayed in the GUI.

---

### Post by g0bez on 2009-01-18
Everything technically is working well, it would appear that my one of my issues is also with the display.

1. I don't know how to describe this, but here it goes. My screen is wrapped about 1/4 of an inch to the right, where the last tiny bit of the right side of my screen is displayed on the left side. I haven't been able to figure out what that is about.

2. Networking drivers are present, and I can get online... I configured eth0 manually. However, when I go thru any gui networking config it shows that i am NOT connected. Also, my wifi won't connect... which is a relatively minor issue, but I'd like to have the networking fixed up.

Otherwise, I'm really excited to get this iMac back alive!

---

### Post by inigomontoya on 2009-01-18
> **g0bez said:**
> Everything technically is working well, it would appear that my one of my issues is also with the display.

1. I don't know how to describe this, but here it goes. My screen is wrapped about 1/4 of an inch to the right, where the last tiny bit of the right side of my screen is displayed on the left side. I haven't been able to figure out what that is about.

2. Networking drivers are present, and I can get online... I configured eth0 manually. However, when I go thru any gui networking config it shows that i am NOT connected. Also, my wifi won't connect... which is a relatively minor issue, but I'd like to have the networking fixed up.

Otherwise, I'm really excited to get this iMac back alive!

The first thing I did was get the newest ati drivers from git, [http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/)

After that I did the first round of updates through update-manager.  I enabled the Broadcom driver in the restricted driver manager then rebooted.  Upon rebooting I saw that my wireless wasn't working quite right so I compiled the latest stable kernel 2.6.28.  Then everything worked.

---

### Post by g0bez on 2009-01-19
Thanks for the tips -- i'll check out the ATI drivers.

Once I try out the new kernel I'll see how the hardware responds. If i understand correctly, the wifi drivers are different than the eth0 drivers. I'll have to look into this more tho.

---

### Post by stream303 on 2009-01-19
> **inigomontoya said:**
> When set to use 24-bit color lots of color banding is apparent as if i'm running in 16-bit mode, that's what i mean.  It is running in 24-bit but it doesn't look that way. So is OSX dithering this before it's displayed?  I saw no color banding while running OSX.  I have a 17inch imac so the resolution is 1440x900.  It is correctly displayed in the GUI.

I wonder what driver xorg is really picking up?  Does the log /var/log/Xorg.0.log show ati, radeon, etc, or just something like fbdev?

---

### Post by stream303 on 2009-01-19
> **g0bez said:**
> 1. I don't know how to describe this, but here it goes. My screen is wrapped about 1/4 of an inch to the right, where the last tiny bit of the right side of my screen is displayed on the left side. I haven't been able to figure out what that is about.

Welcome to my world. :)

I have only seen this effect on my G5 iMac running the opensource nvidia "nv" driver.  Is yours also using nv, and what size is the screen?  Mine is the 20" 1.8ghz model:

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Just so we don't get our wires crossed, which model do you have?

I have spoken to the folks at freedesktop.org, and they confirm that this slight shift to the right is due to a recent commit to nv that fixed some other user's problems with flat panels - unfortunately, that messed it up for us.  So it is upstream of ALL the distros.  If it drives you nuts, only Feisty and below (or Debian Etch 4.0rX) use the older nv driver which didn't have this "fix". :)

> 2. Networking drivers are present, and I can get online... I configured eth0 manually. However, when I go thru any gui networking config it shows that i am NOT connected. Also, my wifi won't connect... which is a relatively minor issue, but I'd like to have the networking fixed up.

I think the big issue here is that if you are going to manually configure your network by manually editing the /etc/network/interfaces file, you need to remove Network Manager.  Or, even if using the standard Gnome network gui setup, NM has to go.  If you DO use network manager, do NOT try to manually configure your /etc/network/interfaces file, or use the gui in System > Network.  That drove me nuts for quite awhile.  I chose to rip out Network Manager.

I'm very interested to see if you are using something other than a 20" G5 iMac running nvidia.

---

### Post by inigomontoya on 2009-01-19
> **stream303 said:**
> I wonder what driver xorg is really picking up?  Does the log /var/log/Xorg.0.log show ati, radeon, etc, or just something like fbdev?

The log shows that it is indeed using the radeon driver.  Strange thing about it is, like with everyone else, if i take a screenshot and view it with another machine that displays 24 bit color correctly, there is no banding.  I would guess that means that it's rendering in 24-bit, but the LCD is not displaying it that way.  It was my understanding that the Dac6Bit option would dither the image to 6 bits from 8 before it was sent to the display eliminating color banding.

---

### Post by stream303 on 2009-01-20
This caught my eye - can you disable DRI and see if that makes a difference? :

[http://forums.gentoo.org/viewtopic.php?t=469455](http://forums.gentoo.org/viewtopic.php?t=469455)

The warning in that xorg.conf mentions not being able to use 24 bits if dri is enabled, and although it is for a different card, and much lower graphics memory, I wonder if that is worth trying just to see...

---

### Post by inigomontoya on 2009-01-21
> **stream303 said:**
> This caught my eye - can you disable DRI and see if that makes a difference? :

[http://forums.gentoo.org/viewtopic.php?t=469455](http://forums.gentoo.org/viewtopic.php?t=469455)

The warning in that xorg.conf mentions not being able to use 24 bits if dri is enabled, and although it is for a different card, and much lower graphics memory, I wonder if that is worth trying just to see...

I disabled DRI and it still shows alot of color banding.  I'm using this as a test image: [http://web.comhem.se/zacabeb/repository/spectrum_rgb.png](http://web.comhem.se/zacabeb/repository/spectrum_rgb.png)

---

