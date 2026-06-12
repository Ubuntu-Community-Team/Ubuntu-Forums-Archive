---
title: "Rare screen flickering after upgrade to 8.04"
date: 2008-05-11
forum: Apple Hardware Users
---

### Post by nopalot on 2008-05-11
Hello,

i have a strange flickering behaviour since i've upgraded my intel mac mini from 7.10 to 8.04.
It happens between once a minute and once every 5/6 Minutes that for a fraction of a second (maybe just one frame/herz) a complete black screen is displayed. (Or maybe its the desctop background can't tell for sure because it's way to fast to recognize)
An other problem i've noticed, that may be related to the flickering is that sometimes all off a sudden, only a black or white screen is displayed, which renders the system unuseable. The black/white screen behaviour happended just twice so far.
Do you have any ideas how to debug or fix the problem?
Please let me know and thanks in advance

---

### Post by spudratic on 2008-05-11
what video card are you using or on board chip set are you using.this is a must since you seem to have video problems.Please try and give as much info as possible.processor,ram, video card.If it makes you feel any better I'm in the same boat roflmao

---

### Post by nopalot on 2008-05-11
Wow, thanks for the quick reply! 
Its a 1.5 years old intel mac mini, with 2 GB RAM and a 32 Bit intel dual core cpu.
Here's the output of lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

Here's the output of "dmesg | grep CPU":
```
[    0.000000] Initializing CPU#0
[   29.173436] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   29.253719] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000 00000000
[   29.253732] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.253734] CPU: L2 cache: 2048K
[   29.253736] CPU: Physical Processor ID: 0
[   29.253738] CPU: Processor Core ID: 0
[   29.253741] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002140 0000c1a9 00000000 00000000 00000000
[   29.618245] CPU0: Intel Genuine Intel(R) CPU            1400  @ 1.83GHz stepping 08
[   29.629086] Initializing CPU#1
[   29.709051] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000 00000000
[   29.709060] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.709061] CPU: L2 cache: 2048K
[   29.709063] CPU: Physical Processor ID: 0
[   29.709065] CPU: Processor Core ID: 1
[   29.709066] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002140 0000c1a9 00000000 00000000 00000000
[   29.709598] CPU1: Intel Genuine Intel(R) CPU            1400  @ 1.83GHz stepping 08
[   29.857021] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   29.877021] Brought up 2 CPUs

```

Any ideas how to fix the problem?

---

### Post by spudratic on 2008-05-11
well I think the trouble is the intel driver for the intel chip sets.I see 945 chip set which is a real problem for ubuntu really at this point any intel video chip runs like shet from what I read.I have the 845g intel chip set and it is slower than snail with compiz enabled watching a video.Most appalling is that this is going to be this way for some time to come.From what I read we need a new kernel with a tt something modual which means a re write of the driver and most likely some tuning of xorg.If i were you I would do a lot of reading on this before you start wasting your time adding programs and eye candy.you can use hardy without desktop effects it is stable but for me this is a waste.the windows preview helps me keep track of things and i like the cube seems easy to manage a lot of open windows without them all being on to of one another.without the cube I can do everything i need to in xp with better video less cpu use and less heat.right now I'm going to uninstall this os and try something else that the effects work in without drving cpu use to 100%.Now i may be wrong but I have been on this since day one of the hardy release with no luck and no answers except from what i stated.This is the best I can do at this time.If I was giving advice I would tell people with intel chipsets not to install hardy stick with gusty for now until sometime in the next decade when they decide to fix it lol.I doubt it will be fixed for ibex the next release maybe the release after that but don't hold your breath.you really need to read on your chip set and what others are saying could just be me but I doubt that after all I read.Also I don't think gusty supported the 945 but I could be wrong and it could be the 965 that was blacklisted in gusty.the bottom line with hardy intel video chip set users beware compiz cube is not an option.

edit :you were using gusty if it worked for you I would reinstall it and stick with that till it all gets sorted out.Please do not take my word for it and check your self.you might come across something I missed.


edit:[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492) this is a good read for you.this is my problem in a nut shell.

---

### Post by nopalot on 2008-05-11
Hi spudratic,
thanks for the info.
One thing I've like to mention is that I've completely disabled all desktop effects. If I don't find a way to fix the problem, I'll downgrade to 7.10. Thanks again.
I'll appreciate any info on this topic!

---

### Post by Brightbelt on 2008-05-11
Hi,
I discovered today that GDM Login themes MIGHT be my problem with screen flickering. I'm on an 24" intel iMac, not a mini, but I have had a similar, though maybe not the same, problem with my screen flickering.  

I just setup Ubuntu on a dual boot on this iMac for the very first time and I noticed that sometimes, booting into Ubuntu, I'd get a screen flicker. Other times, like now, everything was solid. 

I thought I'd tell you about this just in case; it may not apply to you but today, when I changed my Login GDM Theme, (I'm on Gnome), all of the sudden my screen began to flicker.

So I went back in right away, and changed back to what I had before and Voila! the flickering stopped.

Like I said, this might not apply to your case, but I thought I'd share just in case.

Good Luck, Frank B.

---

### Post by cambron on 2008-05-16
I have a imac, 20 inch, intel core 2 duo that I am trying to dual boot Windows XP and Ubuntu (yes, I don't have mac os x on it). I believe it has an ATI Radeon HD 2400 XT 128 MB (im not sure, I dont have access to the imac till a few days).

I downloaded ubuntu 8.04 32-bit, burned it to CD, tried it as liveCD. The results I got was this screen flickering, even after I tried the install option. I let it install with the screen flickering. The boot screen is fine but once it gets past that it will flicker pretty bad the whole time.

[http://ubuntuforums.org/showthread.php?t=793706](http://ubuntuforums.org/showthread.php?t=793706)
This is a message i found that i think will be useful for me when I get the chance to try it on monday next week (on 5-19-2008 ). And when I find what this imac supports for the HorizSync and VertRefresh

---

### Post by phibxr on 2008-05-17
> **nopalot said:**
> Hello,

i have a strange flickering behaviour since i've upgraded my intel mac mini from 7.10 to 8.04.
It happens between once a minute and once every 5/6 Minutes that for a fraction of a second (maybe just one frame/herz) a complete black screen is displayed. (Or maybe its the desctop background can't tell for sure because it's way to fast to recognize)
An other problem i've noticed, that may be related to the flickering is that sometimes all off a sudden, only a black or white screen is displayed, which renders the system unuseable. The black/white screen behaviour happended just twice so far.
Do you have any ideas how to debug or fix the problem?
Please let me know and thanks in advance

I have the same problem. For me it first showed up in Zenwalk while I was still using Ubuntu 7.10, after the video drivers were updated. I tried downgrading them, but the problem was still there. Seems like the curse has finally arrived in Ubuntu too for us Mac Mini users.

Sometimes it will work for several days, but after the first flicker has arrived, there will be more random ones, and finally everything will freeze with a black or gray screen.

```
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```[B]

Edit[/B]: If I'm not mistaken, Intel was aware of this issue several months ago. I'm surprised that nothing has happened yet, so I guess we'll just have to wait it out. Downgrading your drivers *could* work, but I'm not sure on how to do that with the recent updates to Xorg. When I was using Zenwalk I just downloaded the older sources, compiled them and replaced xorg-video-intel (or whatever the name was).

I don't know where to submit bug reports to the developers of the Intel open source driver, and I don't know where to read them, but if anyone does a response in this thread would be appreciated. The current drivers are broken for Mac Mini's with these Intel cards for now it seems, so it would be nice to see them fixed as this is a LTS release.

---

### Post by cambron on 2008-05-21
I was able to fix the problem that I had by installing the ATI drivers using Envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I think I found about Envy from a different post, I don't remember but I followed the instructions on the web site. At the login screen or just after the login screen, I hit control+option+F1 to get to the terminal. Then I ran these two commands to get a script to easily install ATI or nVidia drivers:
```
sudo apt-get install envyng-core
sudo envyng -t
```

Select the option of what to install then reboot the system. I think *apt-get install envyng-gtk* is another install option.

I got the camera to work following instructions from another post, and still needa get the sound to work some how i don't know.

---

### Post by dcviana on 2008-10-06
I have the same problem, but I have a NVIDIA card

```

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)

```

I'm using Ubuntu 8.04 on a notebook with the above video card, 2GB of RAM and an Intel Core DUO T2350

It only happens when using COMPIZ (if I turn it off, the flickering stops) and only after I do something demanding with it, like rotate cube, see some video in fullscreen or something else.

---

### Post by cyberdork33 on 2008-10-06
> **dcviana said:**
> I have the same problem, but I have a NVIDIA card

```

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)

```I'm using Ubuntu 8.04 on a notebook with the above video card, 2GB of RAM and an Intel Core DUO T2350

It only happens when using COMPIZ (if I turn it off, the flickering stops) and only after I do something demanding with it, like rotate cube, see some video in fullscreen or something else.
This thread is quite old, and is in the Apple Users' forum. You might check for more information in the Desktop Effects forum. You can also try out Intrepid and see if the problem persists.

---

### Post by dcviana on 2008-10-07
Thanks, I used the search function and didn't look the date of the thread. Will post on Desktop Effects Forum.

---

### Post by Bramkaandorp on 2008-10-12
I have the same problem, but my computer is a regular pc, with an amd athlon 64 3800+ processor.

Does anyone know a solution to my problem?

Or is it the change in login screen? I use the Paranoid Dust login screen.

Cheers,

Bram

---

