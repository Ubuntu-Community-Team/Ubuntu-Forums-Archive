---
title: "Can't even use live cd b/c of bcm43xx_microcode.fw error"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by sanjay135 on 2007-06-10
I received an Ubuntu and a Kubuntu Feisty Fawn LiveCD a few days ago, but when I try and boot with them, the process is interrupted by a bunch of error lines reading the following:
```
[    125.900000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

Similar errors keep repeating but with different numbers in the brackets. 

I've looked around and I keep hearing stuff about ndiswrappers and fwcutters, but I have no idea what any of this means or what to do with them. 

If anyone could help me out, it'd be much appreciated. 

P.S. If you need my hardware specs or any other info, just tell me what to do and I'll try my best to get it.

UPDATE (07/22/07): I've also recently tried using the Linux Mint and Ubuntu 7.04 alternate text LiveCD's. Linux Mint ran into the same problem. The alternate seemed to be loading fine but it looked (to my amateur eyes) like it was installing so I stopped the process out of fear that it would replace my windows partition as well. Again, any help would be much appreciated! (And is it possible that the error is telling me that my hardware is incompatible with Ubuntu? If so, could someone point me to a good alternative? I chose Ubuntu because it seems incredible and the community is just so enormous, helpful, and knowledgeable.)

---

### Post by schwascore on 2007-06-13
Not that this is a solution, but I had the same problem with a new HP Pavilion dv6000 series. Turns out it is a newer Broadcomm chip that isn't compatible with the bcm43xx driver, but the system still tries to run it as one.  If I figure it out, I'll post back here!

---

### Post by ahchong on 2007-08-01
YO..!!!
i do have the same problem with u. it does related to that ur computer cant use wireless right? well, i use fiesty, and have the same prob. it have been 1month. and i try all method. if u find anything to get wireless work and it work can u pm me ok?

my prob is differ number.
[    69.192026] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

---

### Post by jcaveman on 2007-08-01
Broadcom has been one of the problem vendors for Linux, as they won't release any information on their drivers to the kernel developers.  As such several work arounds have been developed.  NDISWrapper is a wrapper that allows you to work with the Windows XP driver for the modem but takes some additional work to get going.  The bcm43xx-fw-cutter program actually cuts out the firmware that the is uploaded to the card by the Windows drivers so it can be used by the native Linux driver bcm43xx.  I'm currently using the 2.6.22 generic kernel from kernel.org and bcm43xx works with my HP DV6119US and its Broadcom 4311 wireless chip.  I think it may also work with the 2.6.20 kernel that comes with Feisty Fawn, but you'll need to install bcm43xx-fw-cutter package using apt-get or synaptic.

---

### Post by sanjay135 on 2007-08-04
Thanks for the replies. 

It's just that the main problem here is that I can't even really get to the point where I could install fwcutters and the like. I boot from the LiveCD and try to run Ubuntu from within my RAM to test it out on my computer and it won't even let me. If I could get to the point where I could use Synaptic or Automatix, believe me I would have tried.

---

### Post by sanjay135 on 2007-09-23
Does anyone think I'd have better luck with Ubuntu 7.10 or 8.04 LTS? I'll probably try them anyway, and I'm hoping there'll be some improvements, but it'd be nice to have a second (or third or fourth) opinion from someone who actually knows (or has an educated guess).

---

### Post by nb123 on 2007-09-23
I don't know whether any of you has the broadcom 4328 wireless chipset (specifically the Dell Wireless 1500 Draft n card), but I tried the standard drivers that I found on Dell's website with ndiswrapper and they did not seem to work. Specifically, I tried the drivers R151517.exe and R151519.exe. I looked up so many tutorials online but none seemed to get it to work. However, after finding a driver someone recommended on another forum, I got it to work instantly without an issue. I've included a link to the driver here: ---(Note, this is for use with ndiswrapper, I recommend using the latest version)

[http://ftp.us.dell.com/network/R140746.EXE]("http://ftp.us.dell.com/network/R140746.EXE")

If you've tried another method already, you probably have a bcmwl5 driver already with ndiswrapper. You should remove this before installing the driver I've attached as they both have the same name. Hope this helps you.

---

### Post by awing1138 on 2007-10-19
I need to bump this topic.  Perhaps it should be moved to Installation Support?  I get this same error message, and it repeats at seemingly random time intervals.  No GUI ever boots, and no key combination I could think of would kick it out of the loop, save for my computer power button (which, interestingly enough, would cause the OS to start shutting down processes, and would eject the CD, but then would just... freeze, with no graphical output).

Can someone please help?  Not being able to install means not even being able to make changes to the driver blacklist.

For reference:
Ubuntu 7.10 (Gutsy Gibbon) AMD64 - Also, on a separate partition than where I hope to install Gutsy, I have Vista.
Dell Inspiron 1520
Dell 1390 wireless card
Intel Core 2 Duo processor (2.2 GHz)

---

### Post by Sef on 2007-10-19
> The alternate seemed to be loading fine but it looked (to my amateur eyes) like it was installing so I stopped the process out of fear that it would replace my windows partition as well.

Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to install via the alternate cd.

---

### Post by srd on 2007-10-19
install hangs:

click alt+f1 then
sudo -s
killall gdm
rmmod bcm43xx
exit
startx

Install ubuntu
restart 
recovery mode
nano /etc/modprobe.d/blacklist
insert this : blacklist bcm43xx
save click ctrl+x then y
reboot

Your wireless card is problem.

---

### Post by sanjay135 on 2007-10-21
UPDATE: I downloaded 7.10 the day it came out and it works!!! During the boot from the liveCD, it did show at least one bcm43xx_microde error as well as another error I hadn't seen before (something about intel), but it still loaded. The wireless doesn't work and it doesn't recognize my screen as being capable of anything other than 1600x1200 at 61 fps, but I'm just using an ethernet cable now and I believe I can fix the problems with a bit of digging online. If I find that I can get it to work the way I want to, I'll definitely be installing it to a partition on my hard drive.

Thanks to everyone who tried to help!

---

### Post by GamMan on 2008-01-20
I am having the same problem with a HP DV2xxx laptop.  The problem is the Broadcom wireless card, however, I don't understand why the loader doesn't just skip the step.  Is there any way to get the loader to skip it?

In the mean time, I am going to load up my Backtrack CD and see if I cant resolve.

---

### Post by rosegarden78 on 2008-01-20
> **sanjay135 said:**
> I received an Ubuntu and a Kubuntu Feisty Fawn LiveCD a few days ago, but when I try and boot with them, the process is interrupted by a bunch of error lines reading the following:
```
[    125.900000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

Similar errors keep repeating but with different numbers in the brackets. 

I've looked around and I keep hearing stuff about ndiswrappers and fwcutters, but I have no idea what any of this means or what to do with them. 

If anyone could help me out, it'd be much appreciated. 

P.S. If you need my hardware specs or any other info, just tell me what to do and I'll try my best to get it.


You are using an obsolete version.  Please consider downloading or obtaining the latest Ubuntu Gutsy Gibbon 7.10 disc.  If you download it make sure to burn the CD at 4x speed or less to prevent lost time and productivity.

This issue is resolved.  But in case you need more help here's what I did with my BCM43xx under Feisty:

# In a terminal type these commands
1) sudo aptitude install bcm43xx
2) sudo modprobe bcm43xx

NdisWrapper is obsolete.  Do not use it.  FWCutter used to work but not anymore

BCM43xx.deb is the package you need.

If you need more help Google for "Ubuntu BCM43xx" or purchase a Linux-approved wireless card.

Here is Ubuntu's official wiki for BCM43xx

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

