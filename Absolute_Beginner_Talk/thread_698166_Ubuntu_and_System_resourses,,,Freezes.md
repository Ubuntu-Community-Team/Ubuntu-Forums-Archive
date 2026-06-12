---
title: "Ubuntu and System resourses,,,Freezes"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by FrancesL on 2008-02-16
I have been having system freeze and have to hit the power button to get going again. I only bought this laptop about a fortnight ago, and am happy with it BUT I wonder is 512 enough RAM? I asked this Q in another forum and was assured it was. At this precise moment I am showing CPU 13.9% ;Memory and swap history User Mem 252.4MB of 494.7 51% Uses Swap 0 0 0%
Do I need to 'tweak' something? or upgrade RAM or any other suggestions? I find the freeze mostly happens when I and on WWW hav F/fox browsing and Pidgin running.

Using FireFoxMozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.12) Gecko/20080207 Ubuntu/7.10 (gutsy) Firefox/2.0.0.12

Linux Ubuntu 7.10

Intel® Celeron® 540 processor (1.86GHz 1Mb L2 Cache
512MB of DDR2 533 MHz memory,
14.1" WXGA Acer CrystalBrite&#8482; TFT LCD, 1280 x 800 pixel resolution

Mobile Intel® GL960 Express Chipset with integrated 3D graphics, featuring Intel® Graphics Media Accelerator (GMA) X3100 with up to 358 MB of Intel® Dynamic Video Memory Technology 4.0 (8 MB of dedicated system memory, up to 350 MB of shared system memory), supporting Microsoft® DirectX® 9 and DirectX® 10

80GB HDD
Open iConnect DSL connect with Ethernet

**this just happened again. Froze! Mouse still responsive, as was keyboard. Used ctrl>alt>backspace to 'restart'. I did notice the icon for the internet connection was flashing and recall the same thing as happening in previous 'freeze'. I read 'somewhere' (sorry truely can't recall) that there was an issue with the 'startup order' with the network being out of sequence? ie to early in boot command??? could this be a cause? I dont know how to resolve this if so.

---

### Post by njparton on 2008-02-16
There may be something wrong hardware wise. 512MB should be enough although it wouldn't hurt to have more.  How big a swap partition did you create?

Have you tried Xubuntu?

---

### Post by insane_alien on 2008-02-16
512 isenough as long as you are not working with extremely RAM intensive tasks.

my fileserver(well, it does other stuff, but this is the primary function) has 512MB RAM and it rarely slows down because of it.

---

### Post by FrancesL on 2008-02-16
> **njparton said:**
> There may be something wrong hardware wise. 512MB should be enough although it wouldn't hurt to have more.  How big a swap partition did you create?

Have you tried Xubuntu?
I boutgh this notebook as is set up ready to go from store. It came with Ubuntu, I have added the updates as they arrived. I am usind DSL via ethernet for WWW, otherwise I have done nothing
Xubuntu , what advantage do you see in changing to that? Thanks for you time taken to reply

---

### Post by FrancesL on 2008-02-16
> **insane_alien said:**
> 512 isenough as long as you are not working with extremely RAM intensive tasks.

my fileserver(well, it does other stuff, but this is the primary function) has 512MB RAM and it rarely slows down because of it.

I use firefox and admit to being a Club Pogo junky, thats where I 'meetup' with a heap of friends. I use Thunderbird and pidgin. although I last night installed Kopete to give it a shot. I dont run too much at once I dont think ie I am at pogo, will have IM running but that is it. Thanks for your response, anything further would be appreciated

---

### Post by icechen1 on 2008-02-16
Do you have compiz running?if so try to disable it(or some plugins) to see if it runs fine.

---

### Post by FrancesL on 2008-02-16
I just found this with further searching on another forum [www.whirlpool.net.au](www.whirlpool.net.au) , there was discussion regarding the Acer Aspire 4513 which is what I have, and there was talk of a boot issue..quote": to speed boot up go to BIOS setup, find the boot sequence/order etc and change it so the hdd boos before the network adapter. It is not a Linux error either, its a BIOS configuration feature"
next quote " yes it was a boot order- F2 fixed it quickly and then I put the network card as the last boot option rather than the first. Guess the factory must have had it on network boot for a Linux install and never bothered changing it before shipping, yes boot is now faster " end quote.

As I have noted that when  my 'freeze' occurs the network icon is flashing ..could the above be of importance? 

I am only a real newbie to Linux, dont have the confidence without clear instruction to play around inside the terminal.

---

### Post by FrancesL on 2008-02-16
> **icechen1 said:**
> Do you have compiz running?if so try to disable it(or some plugins) to see if it runs fine.

removed compiz thanks for suggestion ...will see how I go

---

