---
title: "ibook G4 ATI Radeon 9550 3D (Beryl) Performance Tweak"
date: 2007-06-02
forum: Apple PPC Users
---

### Post by tcrroadie on 2007-06-02
I am creating this post to help create some more accurate, up-to-date information on the configuration of the xserver when running Beryl on late model ibook G4's.  This post is not necessarily going to be a how-to, but more to the lines of providing information on how to increase 3D performance on ibook's using the ATI Mobile Radeon 9550 video card.  

As many Apple users are discovering, 3D support, including Beryl, does work on the ibook G4 using the open source ATI display driver set.  Beryl will work on Feisty without even touching your xorg.conf file, but 3D performance and window animations tend to be a little slow when using the default xorg configuration. 

I played around a bit and gathered some data when applying only a few select options to my xorg.conf file.  I was amazed at the 3D performance increase I received when applying my selected device options.  Stability does not seem to be affected so far.  

I did not change any settings in my xorg.conf other than the settings listed under Section "Device".  My default Device section from my xorg.conf looked like this. 

```
Section "Device"
        Identifier      "ATI Technologies Inc M11 NV [FireGL Mobility 
T2e]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection
```

First I took a frame rate (FPS) measurement with Beryl on and using the default xorg.conf.  Using glxgears, I measured a frame rate of 365 FPS.  

Next I changed the setting for frame buffer device (UseFBDev) from "true" to "false".  Simply disabling the frame buffer greatly increased my 3D performance.  Glxgears measured a frame rate of 926 FPS. 

Next I added some options to change the AGP settings of my video card.  I added these options.

```
Option          "AGPMode" "4" 
Option          "AGPFastWrite" "true"
```

Since my video card supports AGP 4X, I set AGPMode to 4.  I ran glxgears and measured 950 FPS.  An increase of about 30 FPS from just modifying my AGP settings. 

My last change was adding dynamic clock scaling "DynamicClocks".  Dynamic clock scaling is used to help increase battery life and decrease heat output by clocking down your graphics processor (GPU) when the system detects that the user is not demanding top 3D performance. 
```

Option          "DynamicClocks" "true" 
```

Initially glxgears measued the same frame rate of 950 FPS, but after you are not doing much 3D'ing, the GPU clocks down and the frame rate drops about 10-100 FPS.  After you trigger some 3D affects the GPU scales back up and everything is smooth again.  Dynamic scaling does seem to work very good on my ibook G4.  My battery life does seem longer and my ibook does run a little cooler.  If peak 3D performance is a must, you may want to leave dynamic clock scaling disabled.  

In the end, the Device section of my xorg.conf file looks like this.

```
Section "Device"
        Identifier      "ATI Technologies Inc M11 NV [FireGL Mobility 
T2e]"
        Driver          "radeon"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev" "false"
        Option          "AGPMode" "4" 
        Option          "AGPFastWrite" "true"
        Option          "DynamicClocks" "true" 
EndSection
```

The performance of Beryl on my ibook is much improved with these changes.  The cube and window animations run much smoother.  I did change my chosen video driver from "ati" to "radeon" just to make sure all radeon driver options were available to me an being loaded.  The ati driver is written to use the radeon driver if a radeon card is detected, but I wanted to just make sure.

Now to help clear up some inaccurate information I have found in other post relating to xorg video driver settings for the Apple ibook G4.

Some users will enable Render Acceleration "RenderAccel".  Render Acceleration is not supported on the Radeon 9550, so the xserver will just disable it anyway if you enable it. 

Some users have also enabled Page Flipping "EnablePageFlip".  Page Flipping has been known to be unstable and is disabled by default.  I ran some test with Page Flipping enabled and did not measure or notice any 3D performance increase on my system.  

If I have made any errors in my post, please feel free to respond.  Also if there are any users who have any other tips, please feel free to post.  

Happy Beryling.  :D

---

### Post by luckyd on 2007-06-02
Will this improve my older iBook's ATI Mobility Radeon 9200 preformance as well?

---

### Post by tcrroadie on 2007-06-02
Hi luckyd

It should work just fine on your card.  The man page for the radeon driver states that your card is supported.  

Your ibook also shares the same speed AGP bus as mine, so you can just copy and past the options I used and give it a go.  

See the manual for the radeon driver for more information.

```
man radeon
```

---

### Post by luckyd on 2007-06-02
thanks, it really did make everything run faster, and the biggest thing that the tweaks did was boost the fps by a whole lot :p

---

### Post by reh4c on 2007-06-03
Thanks for the tweaks!  My iBook G4 appears to run much better, especially the ATI graphics card.  The GPU doesn't get nearly as hot.  I'll follow-up after using it more.

---

### Post by reh4c on 2007-06-04
What is the difference between the "ati" and "radeon" drivers?  The ati driver was installed automagically in Feisty, so all I had to do was enable desktop effects.  Can I simply change ati to radeon in xorg.conf...or do I need to install something proprietary?  Thanks.  

Also, are you able to play the game "Powermanga" on your iBook with the above settings?  (Even with default settings, it's very slow.)  This used to be one of my favorite games.  What do you think could cause the slowdown?  I appreciate your help. :D

---

### Post by tcrroadie on 2007-06-04
Hi reh4c

The "ati" driver is written to load the driver "radeon" if it detects a Radeon chipset on your graphics card.  I replaced "ati" with "radeon" just because I'm anel.  It probably isn't necessary, but doesn't hurt anything.

Quote from the ati man page

> ati is an Xorg wrapper driver for ATI video cards. It autodetects whether your hardware has a Radeon, Rage 128, or Mach64 or earlier class of chipset, and loads the radeon(4), r128(4), or atimisc(4) driver as appropriate.

If your view your xorg.log you can see that the radeon driver is actually being loaded even when the "ati" driver is used.  

```
less /var/log/Xorg.0.log
```

You can even search the Xorg.log for a certain term if you like.  For example 

```
grep Radeon /var/log/Xorg.0.log
```

```
less /var/log/Xorg.0.log | grep Radeon
```

See the man pages for the "ati" and "radeon" drivers for more information. 

```
man ati 
```

```
man radeon
```

ATI does not have a proprietary driver for the PPC platform and probably never will, if that is what you were refering to.  The "ati" "radeon" drivers are open source drivers created by the community.  

I have never tried to play the game Powermanga on my ibook.  In fact, I haven't tried playing any 3D games on my ibook yet.  I was actually thinking last night, wondering how well some of the 3D games available for Linux would run on my ibook.  

To help improve performance when playing games on your ibook, you could try disabling the Option "DynamicClocks" "true" in your xorg.conf to help improve your frame rate.

```
Option   "DynamicClocks"  "false"
```

---

### Post by reh4c on 2007-06-04
Thanks, tcrroadie.  I appreciate the ati and command line info.  I was amazed on my iBook that the community graphics driver was loaded automatically with DRI enabled.  Also, it was a pleasant surprise when I enabled Desktops Effects through the GUI and bouncy menus just worked.  After checking Synaptic, I found that Compiz was installed vice Beryl.  I've only noticed a couple of possible "bugs," such as the shift button not working properly after suspending my laptop (i.e. can't shift to make capital letters).  If "fancy" desktop effects and more reliable wireless networking (network manager + bcm43xx driver) can be achieved, the ibook would be an ideal Linux platform.  It's very impressive as-is.

---

