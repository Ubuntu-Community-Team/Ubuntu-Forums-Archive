---
title: "Ubuntu Newbie - Install Trouble"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by mmmfottrell on 2007-10-19
[B]SEE BELOW THANKS
[/B]



[I]Hello. Just decided to switch from Windows. Installed 7.10.

Completed installation a little bit ago, and now when i try to boot to HD screen just goes blank. I manage to get past GRUB, but after that I go from some commands to blank screen. I don't even get to loading screen. After a while it just turns off.

I am using an HP zd8000 laptop, 1g ram, ATI mobile graphics card, 3.2 ghz pentium processor. 

Any help is much appreciated :KS[/I]

---

### Post by Qwerty_ on 2007-10-19
Hmm this appears to be a recurring problem.

---

### Post by mmmfottrell on 2007-10-19
Continuing with my troubleshooting. :D 

Still takes quite a while for Ubuntu to start up and it goes from blank screen to the login screen. No loading splash or anything.

Wireless. I have found (in the Restricted Drivers Manager) my ATI card and my Broadcom wireless.

When attempting to add the ATI card I get an error of :

[I]The software source for the package

   xorg-driver-fglrx

 is not enabled.[/I]

When attempting to add the firmware for my card I get an error of:

[I]The software source for the package

   bcm43xx-fwcutter

 is not enabled.
[/I]

---

### Post by Bennett2005 on 2007-10-19
This is the same problem I'm having, check out the post I made earlier this morning.

[http://ubuntuforums.org/showthread.php?t=581012](http://ubuntuforums.org/showthread.php?t=581012)

I haven't had a chance to sit down and go through it in detail yet.

---

### Post by mmmfottrell on 2007-10-19
Thanks I will try those. I still need help with my wireless!! Damn Broadcom loves M$.

---

### Post by Licurgo on 2007-10-19
mmmfottrel:
Was is the output of the command **dmesg**:
This could clarify what is going on

---

### Post by mmmfottrell on 2007-10-19
the output is pages and pages but i think the important part is this:

[  131.712045] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  134.221194] [drm] Setting GART location based on new memory map
[  134.221633] [drm] Loading R300 Microcode
[  134.221683] [drm] writeback test succeeded in 1 usecs
[  137.083548] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  139.808181] eth0: no IPv6 routers present
[  152.664700] UDF-fs: No VRS found
[  152.738930] ISO 9660 Extensions: Microsoft Joliet Level 3
[  152.818987] ISO 9660 Extensions: RRIP_1991A
[  159.060590] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  181.051902] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  203.039781] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  225.081356] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


and that error continues for quite a while

---

### Post by mmmfottrell on 2007-10-19
so my wireless now works :D 

i went to get some lunch and lookup info about my hardware at a friends house and when i came back it just allowed me to download the firmware without a problem.

HOWEVER i have seen some people saying that if the previous work around, (cant remember the name) for broadcom wireless devices provided better connection. is this true?

still working on the black screen in between GRUB and the login screen. seems to be a common problem atm for many people.

---

