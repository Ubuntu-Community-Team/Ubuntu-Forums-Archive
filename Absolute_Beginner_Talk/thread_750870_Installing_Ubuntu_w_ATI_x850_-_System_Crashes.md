---
title: "Installing Ubuntu w/ ATI x850 - System Crashes"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by LipidSama on 2008-04-09
I am new to Linux so I will apologize first for my lack of terminology and skill. If I say something or don't explain something properly let me know and I will try to rephrase it so you guys can better understand and maybe you can help me better in the end. :)

I have had  M$ Windows XP on my 'off computer' for about 2 years now. In hopes of broadening my computer knowledge I decided to install Ubuntu. I downloaded Text-based 7.10 AMD64 ISO from the website and installed the image to a DVD/r. I installed the OS fine. Just jumping back a second. I originally got the normal version of the ISO, but the cd wouldn't even load, so I did some research and some <searches> in this forum and found out that there was some graphical bug with ATi's. So I got the text based cd, and installed it. Now when I go to restart the PC after it tells me to remove the cd from the install, the normal energy power saver window in bio's comes up and it goes through the numbers. When it gets to the loading ubuntu stuff  my caps lock and scroll lock lights just blink, and my monitor says unable to read single and goes dead. I was looking online and people where saying to install envy, and log into safe mode. This is probably where the newb stuff comes in. Is there a simple fix to this?, or a simple key binding for safe mode? because I don't see anything labeled safe mode. Any tips of suggestions would be most appreciated.

Im not sure the exact stats:
AMD64
2 gigs of ram
4 HDD's
ATI x850x
View Sonic Monitor

If you need any more information to help diagnosis me let me know :)

---

### Post by joe.turion64x2 on 2008-04-10
> **LipidSama said:**
> I am new to Linux so I will apologize first for my lack of terminology and skill. If I say something or don't explain something properly let me know and I will try to rephrase it so you guys can better understand and maybe you can help me better in the end. :)

I have had  M$ Windows XP on my 'off computer' for about 2 years now. In hopes of broadening my computer knowledge I decided to install Ubuntu. I downloaded Text-based 7.10 AMD64 ISO from the website and installed the image to a DVD/r. I installed the OS fine. Just jumping back a second. I originally got the normal version of the ISO, but the cd wouldn't even load, so I did some research and some <searches> in this forum and found out that there was some graphical bug with ATi's. So I got the text based cd, and installed it. Now when I go to restart the PC after it tells me to remove the cd from the install, the normal energy power saver window in bio's comes up and it goes through the numbers. When it gets to the loading ubuntu stuff  my caps lock and scroll lock lights just blink, and my monitor says unable to read single and goes dead. I was looking online and people where saying to install envy, and log into safe mode. This is probably where the newb stuff comes in. Is there a simple fix to this?, or a simple key binding for safe mode? because I don't see anything labeled safe mode. Any tips of suggestions would be most appreciated.

Im not sure the exact stats:
AMD64
2 gigs of ram
4 HDD's
ATI x850x
View Sonic Monitor

If you need any more information to help diagnosis me let me know :)
That's a curious problem to be honest. From the description you have not been able to boot Ubuntu properly.

A kernel parameter that has saved my neck several times with non-booting machines is *noapic* which does something about power management (I guess disables advanced features). I suggest you to try to boot the liveCD (or DVD for that matter) making sure you pass that parameter to the kernel. From what I recall of an Ubuntu liveCD you should be able to press F6 to access kernel parameters, and type noapic, then hit enter.

If that allows your machine to boot the DVD then you can try installing (and hopefully it's retain the parameter), if it doesn't then an alternative action would be needed.

Good luck.
Joe.

---

### Post by LipidSama on 2008-04-10
First off thank you very much for your help. However I typed that in, and the F6 feature was there. However it still goes to a black screen.

---

### Post by joe.turion64x2 on 2008-04-10
> **LipidSama said:**
> First off thank you very much for your help. However I typed that in, and the F6 feature was there. However it still goes to a black screen.
It's alright. You know, there is this another command *nolapic*, parhaps you can try both together.

Just now another idea came to my mind, perhaps the parameter *xdriver=radeon* could work. I remember it from my Sabayon days (know it is not Ubuntu but you can try).

Good luck.
Joe.

---

