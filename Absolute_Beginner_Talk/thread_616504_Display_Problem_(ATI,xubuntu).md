---
title: "Display Problem (ATI,xubuntu)"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Walker T on 2007-11-18
Alright, here goes.

A few days ago I decided to familiarise myself with Linux, so I put in another HD in my mid-end desktop system and installed Xubuntu (A website recommended Ubuntu, and I decided on Xubuntu for the lighter interface (xfce)) with the Live CD. Quick install, no problems there, at all. Booted up perfectly, so I slowly started experimenting.

Now, I've tried several programs that were included with the installation. I've installed Totem gstreamer, flash player, and I followed the guide for manual installation of ATI drivers after I ran into the first hitch:

At first I noticed that the visualisation effect in Totem clearly wasn't working right. It had a significant delay and constant low fps, as well as a conspicuous green line vertically across the visualisation screen.

Naturally, I spent several hours on google searching for the fountain of youth, but was unable to find an answer or a HowTo/guide covering it. Then I tried playing  a movie and the video output started about a third below the top of the output box, bleeding way outside the Totem window. No freeze, lockup or performance loss. The part of the movie that was actually displayed in the proper place ran just fine, no strange color issues or anything of that matter.

So, then I thought, obviously there's a problem. I decided to check the 'Screens and Graphics'. Graphics card: ATI Radeon fbdev, Driver: fglrx. As much as I know, that sounds fine, but I also checked the verification steps from the installation guide:

fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1800 Series
OpenGL version string: 2.0.6958

This information appeared correct according to the guide. Alright. Then I noticed the 'Screen' tab of the 'Screen and Graphics Preferences', and the information it had about my monitors. (Primary is a Hyundai Q90U 19" DVI, Secondary is a Dell 1909FP 19" DVI. Both connected to the an X1800 XT via DVI). Apparently, Screen 1 is a Plug 'n' Play model. Yeah, sure, seeing as neither of my two screen models appear in the list I left it as that. Resolution 1280x1024. Works, correct colours and size, but windows get trails when moved around. Then, it claimed to be displaying at 75Hz. Now, neither of the monitors support refresh rates above 65Hz, so I selected 60Hz in the drop-down menu and hit 'Test'.

Woh. Black screen. Secondary monitor remains black (makes sense, it's set on 'Disabled') where as the primary monitor comes back with the cursor as a cross, no desktop or icons, just a black/grey erroneous pattern, behaving just like a screen would if it was set to run at a completely wrong refresh rate. Up in the left corner is a  dialog with the standard 'Settings reverted in 15 seconds'. Naturally, I pressed revert and things went back to normal.

Now, normal shouldn't be normal. Right now, both monitors are turned on displaying the same thing, even though Screen 2 is set to disabled. I've tried testing a lot of different settings but all with the same result. I haven't pressed OK after changing settings, because I have a feeling that'd break something.

I hope that's a good enough explanation of my problem(s). Before posting this I made good use of the similar thread search function (almost better than the normal search function!), read a lot of other threads, the Is Ubuntu for me thread (I agree. the water is warm and very comfortable) and some more random posts.

As for me, I'm an advanced Windows user, been with it since DOS (If I'd skipped Win98 I'd have had more hair on my head today). I've built computer systems from hardware I chose myself, and probably done a lot of things with a PC that you shouldn't.

Granted, I'm new to the Linux scene, but after what I've seen so far I'm very much inclined to use it for my non-gaming activities (I almost fell off my chair when I saw how fast it boots).

I hope I followed the rules with this post and provided the correct information. If not, I shouldn't have any problems producing it.

Thanks in advance!

 - Walker

System Specs:
Xubuntu 7.10 'Gutsy Gibbon' (Kernel Linux 2.6.22-14-generic)
Intel Pentium 4 3.4GHz
ATI X1800 XT (ati-driver-installer-8.42.3-x86.x86_64)
Creative SB Audigy 2
Wired LAN Network Card (haven't got the model name on the top of my head)

Screen 1: Hyundai Q90U 19" DVI
Screen 2: Dell 1909FP 19" DVI

---

### Post by gn2 on 2007-11-18
Try disabling all the Compiz 3D effects and see if that makes a difference.

Try replacing the graphics driver using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Are you using 64-bit Xubuntu, and have you tried 32-bit?

---

### Post by Vadi on 2007-11-18
I'd say that you're lucky that card even worked. I have a friend who'd gladly use Ubuntu, but ATI has really poor linux drivers for that card and the LiveCD can't even display anything for her.

---

### Post by Walker T on 2007-11-18
Yes, after reading how much trouble others have had with this card I figured the only thing to do would be to wait in case an update comes out specifically for it. Sure wish I'd chosen nVidia instead of ATI back then. For many reaons.

I'm quite certain it's 32-bit ('PC (Intel x86) desktop CD' was the download option I chose at the cd image download page).

I haven't installed Compiz. Of course, I've looked at Beryl and all those Cube programs, but ultimately I doubt I'd like it.

Reading up on envy right now.

---

### Post by gn2 on 2007-11-18
> **Walker T said:**
> 
ATI X1800 XT (ati-driver-installer-8.42.3-x86.x86_64)


This ( _64 ) would seem to indicate a 64-bit graphics driver is installed ?

Compiz is installed by default in 7.10.

---

### Post by Walker T on 2007-11-18
I believe the 'x86.x86_64' means that it's intended for both. At the ATI Drivers download page both 64-bit and 32-bit Linux driver requests for X1800 end up at the same page.

As for compiz, it says it's not installed. pkg-config is unable to find it, as well.

---

