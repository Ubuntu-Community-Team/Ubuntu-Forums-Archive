---
title: "Ubuntu Battery Life?"
date: 2014-03-11
forum: Apple Hardware Users
---

### Post by d4m1r on 2014-03-11
Hey guys, I am sure I am not the only one having this problem....Unfortunately, I feel like this is more "as designed" than a "bug" or something I can fix. Basically, I have a triple booted laptop (rEFit) and get the below battery lives under each respective OS;

-OS X = 6-7 hours
-Windows 7 = 4-5 hours
-Ubuntu 12.04 = 2-3 hours

This is all with a 2012 Core i5 Macbook Pro and light internet/email browsing via Wifi. Why such the discrepancies if the hardware (including the battery) are the same? Is OS X really **that** much more optimized in regards to battery life than Ubuntu?? It basically means I never use Ubuntu while on the go, only OS X for optimal power efficiency :(

---

### Post by ian-weisser on 2014-03-11
> **d4m1r said:**
> Is OS X really **that** much more optimized in regards to battery life than Ubuntu?

For *your specific hardware*? Perhaps so.

If you can identify some of the power-hogging services and applications in Ubuntu, and/or some of the power-saving optimizations that Ubuntu lacks, the Ubuntu developers would love to know more detail.
We don't try  to create a power-hogging distro.
And there's not a magic "power-saving" mode.

---

### Post by zircon_34 on 2014-03-11
I installed laptop-mode-tools, check my [thread]("http://ubuntuforums.org/showthread.php?t=2208563"), it increased my battery life on macbook air from <2h to >4.5-5 hours!

---

### Post by Lars Noodén on 2014-03-11
> **zircon_34 said:**
> I installed laptop-mode-tools, check my [thread]("http://ubuntuforums.org/showthread.php?t=2208563"), it increased my battery life on macbook air from <2h to >4.5-5 hours!

I'll have to give that a try.  I have the same battery issues as  d4m1r, minus Windows of course.  I also see that the battery starts to charge for a few seconds to a few minutes for no apparent reason.

---

### Post by zircon_34 on 2014-03-11
and you may want to try [powertop]("https://01.org/powertop"), to check what program consumes a lot of battery;) , maybe also switching off bluetooth if you are not using it.

---

### Post by d4m1r on 2014-03-12
> **zircon_34 said:**
> I installed laptop-mode-tools, check my [thread]("http://ubuntuforums.org/showthread.php?t=2208563"), it increased my battery life on macbook air from <2h to >4.5-5 hours!

Thanks for the tips guys and I'll try out laptop-mode-tools I guess. FYI, bluetooth and basically most other things are already disabled and my brightness is usually at 30-40% only and I was still only getting 2-3 hours :(

Anyway, I wanted to ask how is your performance now with the extended battery life? I ask because I have Juniper installed but it doesn't seem to do much AND causes noticeable lag when my Macbook is unplugged....

---

### Post by zircon_34 on 2014-03-12
> **d4m1r said:**
> 

Anyway, I wanted to ask how is your performance now with the extended battery life? 

I was also worried about that before installing the tool because I never tried it before, but I did not have to tweak any setting and did not see any performance degradation. It just improved my battery life, and thats what I was looking for. However, I did not try it on a macbook pro. 

For the tool (Juniper) you are currently using, I suggest that either you read the manual or try the forum (separate specific thread) to see if there is some trouble shooting for your problem, or deinstall it, because to my opinion this is NOT satisfactory. 

I hope you guys manage to increase your battery life:), because this has been the cause for me not to switch to linux for a while, but that was a game changer for me. I also use xfce (XUbuntu) that may also use less battery.

---

### Post by d4m1r on 2014-04-05
Fixed! I knew there had to be a way.....

Anyway, I went ahead and installed laptop-mode-tools according to [THIS]("http://www.webupd8.org/2014/01/install-laptop-mode-tools-164-with.html") guide and I am now getting 3-4 hours of battery life under Ubuntu :) Didn't require any configuration and no noticeable performance hit...

---

