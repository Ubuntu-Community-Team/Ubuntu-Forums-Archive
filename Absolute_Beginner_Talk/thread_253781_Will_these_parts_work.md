---
title: "Will these parts work?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Buddha443556 on 2006-09-08
Hi,

I'm about to order a new PC. Money is tight and this is what I've come up with:

[INDENT]**Motherboard:** Gigabyte GA-M55plus-S3G AMD Socket AM2 ATX, GeForce 6100 Chipset, Marvell 88E1116 Gigabit Ethernet controller, Realtek ALC883 Audio Codec[/INDENT]
Plan on using the on-board video, LAN and sound. Am I hoping for too much?


[INDENT]**Processor:** AMD Sempron 64 3000+ Manila Socket AM2 Processor SDA3000CNBOX, 1.6 GHz, 1600MHz HT, 256KB L2 Cache. 	Arctic Silver Ceramique.[/INDENT]
I live Florida without AC, 95+ degrees F throughout the Summer even at night. Choose this processor (and the motherboard) to down shift using powernow. At it's Min P-State the processor is down to only 19 watts. From what I read this should work, I'm I right? 


[INDENT]**Memory:** Kingston DDR2 1GB(2x512MB) Computer Memory, 533MHz PC2-4200 Non-ECC CL4, KVR533D2N4K2/1G[/INDENT]
I think I got the right memory but I'm willing to be corrected. :mrgreen: 


[INDENT]**Hard Drive:** Western Digital Caviar SE SATA 250GB Hard Drives WD2500JS, 300 MB/s, 7200 RPM, 8MB Cache. OEM[/INDENT]
Well, will it work with the Ubuntu 6.06?


[INDENT]**DVD-RW:** NEC ND-3550A[/INDENT]
As long as it's not DOA my guess is it should work.


[INDENT]**Case:** Antec Solution Super Mid-Tower ATX Case SLK3800B, w/ 400W SmartPower 2.0 PSU, 120mm Fan, Adding 2nd 120mm Fan[/INDENT]
Not too sure about that power supply? ... but it comes with the case.


That's about it except keyboard, mouse (both PS/2) and a 17" LCD. So do you think it will all work together with Ubuntu? This will be my first Linux computer. I would appreciate any advice.

Buddha

---

### Post by daniel of sarnia on 2006-09-08
I have a problem with my marvell gigabit gthernet controller on my asus mother bored, I have not botherd to try and get it to work. It sees it, but won't conect. I just through in a old 100 mbit card. But other then that you should be okay.

---

### Post by bodhi.zazen on 2006-09-08
Watch that CPU. Take a look at Ubuntu for 64 bit processors first, you may just end up running 32 bit software. Not much $ savings I bet, but every bit counts and you should know what you are getting into.

---

### Post by Buddha443556 on 2006-09-08
> I have a problem with my marvell gigabit gthernet controller on my asus mother bored, I have not botherd to try and get it to work. It sees it, but won't conect. I just through in a old 100 mbit card. But other then that you should be okay.

Thanks for the heads up about the gigabit ethernet controller and the encouraging words. That Marvell 88E1116 does look a little iffy.

But I did find this ...
> 
On Fri, 18 Aug 2006 21:46:47 +0000, Wes Newell wrote:
> I've tried everything for a couple of days to get this workinhg with no
> luck. Onboard 1000Mbit nic on Gigabyte M55Plus-S3G. I've downloaded the
> Nforce drivers Nvidia but they won't compile. Anyone out there got it
> working. Any board with the 430 chipset and Marvell 88E1116 should use the
> same driver. Got a name for it if it exist yet? Distro doesn't matter as
> I'm running kernel 2.6.17.8. Got the nvidia graphics driver working, but
> this is eating my lunch.

Crap. After all this grief all I needed to do was load the new module
(**forcedeth**). I didn't see it because it was **listed under 100Mbit** support
in the kernel sources. Working fine now. Sorry to bother everyone.

> Watch that CPU.
My biggest worry.

---

### Post by dunklegend on 2006-09-08
I have an Athlon 64 X2 3800+ which is a 64 bits double core processor.
I installed Ubuntu 6.06 on it (the 64 bit version) and it worked fine.
My only complaint is that the 6.06 version doesn't run 32 bit applications.
I read that it will run the 32 bit apps for the next version (6.10 I think)

Right now I installed the 6.06 version but the 32 bit flavor and it also runs fine.

I think that processor will be fine.

---

### Post by Buddha443556 on 2006-09-09
> My only complaint is that the 6.06 version doesn't run 32 bit applications.
I read that it will run the 32 bit apps for the next version (6.10 I think)

I was wondering what the difference was between 32 and 64 bit Ubuntu. Think I'll stick with the 32bit versions as you suggest.

I would love to run a dual core like yours but installing AC would just kill my budget. :)

---

### Post by Chemroydal Tissue on 2006-09-09
> **Buddha443556 said:**
> **Motherboard:** Gigabyte GA-M55plus-S3G AMD Socket AM2 ATX, GeForce 6100 Chipset, Marvell 88E1116 Gigabit Ethernet controller, Realtek ALC883 Audio Codec[/INDENT]
Plan on using the on-board video, LAN and sound. Am I hoping for too much?

The Marvell Ethernet controller 88E8001 on my Asus A8N worked out-of-the-box (Dapper64), but this board also has an Nvidia CK804 controller, which is what I ended up using (purely by chance). I've heard of others having problems with Marvell ethernet controllers in releases after Warty (some seem to have been fixed for Dapper?). It was a kernel issue, not an Ubuntu issue, as I understand, so I'm not sure whether or not it's been fixed. It only mattered for me during OS installation anyway, since I'm using a Belkin wireless network adapter (Broadcom 4318 chipset).

I had a problem initially with my LCD monitor, (I bought it when I was using Hoary), but it's Just Worked ever since (it's a Proview 19").

---

### Post by Buddha443556 on 2006-09-09
> It was a kernel issue, not an Ubuntu issue ...
Looks fixable or fixed ... So I did it.

I just ordered this setup, so in about week I should be back to tell you how the Ubuntu installation went. I would like to thank everyone for their replies - they all helped.

---

