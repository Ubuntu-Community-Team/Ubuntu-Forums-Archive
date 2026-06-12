---
title: "Installation problem on Dell[Solved]"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by CJ56 on 2007-11-05
I hope this question hasn't already been done to death somewhere else - apologies if it has -

I'm running a Dell Dimension 2400, 512 RAM + P4

I can't get Ubuntu (either 6.10 or 7.10, which is the one I want to install) to get past the initial live  desktop. It takes forever to load up & then just hangs. This has also happened with Zenwalk and Mepis. Knoppix & Puppy live CDs work fine running from RAM. I'm presuming that I've got enough computing power - it runs Xp ok. But it just doesn't want to install any flavour of Linux. i've installed Ubuntu 7.10 very happily on a couple of other non-Dell machines, so I reckon the disc's ok.

Is there something obvious I should be doing? At BIOS level?

Any advice gratefully received...

---

### Post by undadecor on 2007-11-05
Not sure how to get the live cd to work.  But whenever I have that problem I just use the Alternate Install disc image and install Ubuntu that way.

---

### Post by amingv on 2007-11-06
Hello,

I used to have that problem with a Dimension 3000 Desktop, and was able to run the LiveCD and make the installation after I made some changes in the BIOS:

> 
Memory Information>AGP Aperture = 64MB //<-You may or may not have to fiddle whith this depending on your specs, but try it.

CPU Information>CPU Speed = Normal

Integrated Devices>Onboard Video Buffer = 8MB

Fast Boot = ON

OS Install Mode = OFF

Limit CPUID Value = Enabled

That did the trick for me, tell me how it does for you...

Edit:PD: This changes should not harm your WXP performance.

---

### Post by CJ56 on 2007-11-20
Many thanks for those suggestions -

I'll let you know how I get on!

CJ

---

### Post by CJ56 on 2007-11-21
Just to update & if it'll help anyone else -

I checked out the BIOS as above, it seemed okay

Did an alternate install of Ubuntu 7.10 - it worked first time....! 

(Sometimes the answer's just staring you in the face...)

Many thanks again

CJ

---

