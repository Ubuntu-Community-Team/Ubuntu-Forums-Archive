---
title: "ATI Driver: Can't SUSPEND/HIBERNATE"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by EJacqmain on 2008-03-18
Here's my situation:

I installed Ubuntu (7.10) on my Dell Inspiron 1501 a few days ago (partitioned, 50% Ubuntu/50% XP).  Installation went smoothly. 

>STATS:  

DELL INSPIRON 1501
120gb HD (partitioned 50%)
ATI Radeon Xpress 1150 graphics
AMD Turion 64 X2 processor


When ubuntu booted up for the first time, the restriced driver manager told me that i needed to install the restricted driver for my **ATI Radeon Xpress 1150 graphics card** and my wireless card.  It installed the driver and was rebooted. 

Now i encountered my first problem; When i tried to enable desktop effects, i would get a message saying "The composite extention is not available" in otherwords, compiz not installed.    So, i found a forum that told me how to install compiz, so I followed the directions and compiz was installed.   I was able to enable and customize my desktop effects (happiness).     I finished playing around with the settings after a while and decided to put the computer into suspend (which it had done before successfully).  

Immediately after hitting the suspend button, my desktop folded into a paper airplane, the hard drive shut off, screen turned black, mouse turned off, and wifi light went out, but the power light stayed lit and  the fan kept going.  I waited a minute and it was still sitting there doing the same thing. I held down the power button and killed it.  Fantastic...         

I booted it back up and posted on here about what just happened. I turned off desktop effects and tried to suspend again to determine if it was a problem with compiz. NO LUCK    
same thing happened...

I booted it back up again. I tried to hibernate...   WHOA!... everything but the motherboard and graphics card turned off, and the screen remained on while showing a mess of color-changing lines and shapes.

Killed it and rebooted. This time, I disabled the restricted driver and restarted. After rebooting, suspend WORKED and compiz worked (but VERY VERY SLOOOOOOWWWLY).       

Thus, **the problem is not compiz, but clearly the restricted driver** , which was apparently modified when i installed compiz. Because _suspend worked with this driver_ before i installed compiz!!!...     I followed the directions on the forum EXACTLY, and maybe i entered a code that didn't belong.    (I am a noob btw)

SOMEONE ANSWER THESE QUESTIONS!!!

1) When i "disable" a driver, does it actually "uninstall" it?
2) Does disabling a driver and re-enabling it completely replace it? If i reboot with the driver enabled (since I've disabled it), will it solve the problem? (havent tried yet)
3) Should I uninstall and reinstall Compiz? How?
4) What driver did the Restricted drivers manager install: OPEN SOURCE or CLOSED SOURCE? Would I have better luck with the other? How would I get the other one?

You see how I'm confused...   HELP!

---

### Post by spectrevk on 2008-03-18
I'm having a similar problem with my Compaq Presario V5000. I tried disabling the driver, but in my case the problem persists.

---

### Post by EJacqmain on 2008-03-22
I disabled the restricted driver, rebooted, and installed Envy. I used Envy to install the latest ATI driver. When i restarted, (after bios and OS selection) all I got was a flash of text in large font and a blank screen.   now what...   

 All i have to work with is recovery mode.    I think i missed a step before installing envy. I think i was supposed to get rid of xserver or something.       Is there anything i can do with the command line, or am i going to just have to completely reinstall ubuntu.

---

