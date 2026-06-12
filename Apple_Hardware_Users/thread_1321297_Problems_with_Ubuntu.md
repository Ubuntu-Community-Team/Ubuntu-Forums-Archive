---
title: "Problems with Ubuntu"
date: 2009-11-09
forum: Apple Hardware Users
---

### Post by Nadav34 on 2009-11-09
Hello,

 I have a Mac Pro 3,1 2008 model. I downloaded the AMD64 or 64-bit version. While it booted up completly and gave me the install screen, I clicked on the install screen and after a few minutes my monitor went black and everything stopped. Has anyone ever had this problem before? I am doing a straight install of ubuntu without bootcamp or a bootloader.

To clarify again, when I select english as the main language and click "install ubuntu" - a few things come up and then the screen goes entirely black. The dvd also stops spinning as well.

What could be the problem here?

---

### Post by linuxopjemac on 2009-11-10
I recommend the 32 bit version. I read problems with the 64-bit.

---

### Post by jnorthr on 2009-11-10
if it were me, i'd create a live CD of the latest release and run from there for a while before trying a full install. Then you could confirm what works and what does not work, before you spend time doing a full install. And it would reduce the likelyhood of blitzing your current system, which you have already backed up, haven't you ?
;)

---

### Post by Stormspace on 2009-11-10
> **Nadav34 said:**
> Hello,

 I have a Mac Pro 3,1 2008 model. I downloaded the AMD64 or 64-bit version. While it booted up completly and gave me the install screen, I clicked on the install screen and after a few minutes my monitor went black and everything stopped. Has anyone ever had this problem before? I am doing a straight install of ubuntu without bootcamp or a bootloader.

To clarify again, when I select english as the main language and click "install ubuntu" - a few things come up and then the screen goes entirely black. The dvd also stops spinning as well.

What could be the problem here?
I bet you if you hit the space bar you'll see an initramfs prompt. I believe this is being caused by the live CD failing to load. It's happened to me as well. I'm planing to try an alternate install disk.

---

### Post by Nadav34 on 2009-11-14
Hello again,

 I have a 2008 mac pro and for some reason when I get to the install screen of ubuntu and under options select NORMAL for video mode, it doesn't boot at all. But, when I select safemode, it works. I have 9.10 Ubuntu and I also just learned that unlike freebsd or others Ubuntu requires an internet connection to install wifi. 

I found a workaround for installing the wifi, but one has to be loaded in the liveCD to be able to do it. As far as video is concerned, is there a way to get out of failsafe mode into normal mode? I tried installing the fgclrx(sp of driver) of ubuntu, but it locks up my computer in doing so. I also downloaded the ATI Radeon 4800 series driver for linux as well.

So, main problems I would like to solve:

Being able to use normal video mode(LiveCD), and if I don't have internet installed at the time, how do I install my Airport express wireless card's driver(inside mac pro)?

Also, as for bluetooth keyboard, the mouse is fully functional, but the Apple wireless keyboard I have(model A1148) keeps continuing to fail on recognition.

Thanks,
Nadav

---

### Post by Nadav34 on 2009-11-14
What happens when you go to select NORMAL mode(F4), versus failsafe mode?

---

