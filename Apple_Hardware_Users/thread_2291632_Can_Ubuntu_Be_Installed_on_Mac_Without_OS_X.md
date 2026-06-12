---
title: "Can Ubuntu Be Installed on Mac Without OS X?"
date: 2015-08-21
forum: Apple Hardware Users
---

### Post by HDTimeshifter on 2015-08-21
I was given a Mac Pro (2010 Xeon 2.8 GHz) without a hard drive and was wondering if I can buy an SSD (or install a blank hard drive) and install Ubuntu on it. I also have a fairly old Mac Book Pro (2.4 GHz Core2 Duo) that also doesn't have a hard drive. I did some Google searches, and found a page about installing Ubuntu on a Mac Book Pro, however, the page I found about installing on a Mac requires booting into OS X during the install. If Ubuntu can be installed on a Mac Book Pro without OS X, I think it should be possible and easier on a Mac Pro, especially as it doesn't have to support the track pad, retina display, or fans (I'm guessing constantly running fans on the tower would be ok). I've been a primary Ubuntu house since 2008, running it on my main desktop (2.4 GHz Q6600 quad core) with a second hard drive for the rare dual boot to Windows 7. My server that I use mainly for backups is also running Ubuntu. I also have a 1.67 GHz Core 2 Duo laptop (upgraded from Vista to Windows 7) that runs like a dog and if restoring with backup DVDs doesn't fix it will wipe and install Ubuntu to see if that makes it usable. I think I can buy OS X Snow Leopard for $20 a copy and upgrade to the current OS X for free for these Macs, but would rather keep everything primary Ubuntu, especially if I replace my main PC with the Mac Pro.

---

### Post by soyoboi on 2015-08-21
The short answer, Yes.

---

### Post by mystics on 2015-08-22
If they're telling you to boot into OS X, then I'm guessing it is to do a lot of the pre-installation stuff. In other words, you do things like make an installable USB and partition the hard drive in OS X before installing Linux. If you're working from a new hard drive and can make an installable from another computer, then there's no need to get OS X if you don't want it.

---

### Post by HDTimeshifter on 2015-08-24
Then I assume I can make a bootable USB from a Linux computer and the partitions will be created as usual during the install (no need for OS X partition)? And it will create a system that boots directly from EFI and not BIOS emulation? And I don't need any special hacks for it to handle the Mac hardware?

---

### Post by luciano.x on 2015-08-26
^
Yes. Yes. Don't know. What is your current hardware?

---

### Post by HDTimeshifter on 2015-08-26
Mac Pro (2010 Xeon 2.8 GHz) as mentioned in the OP. Don't yet have a video card or hard drive in it, but was going to either install a hard drive or SSD and try out an older video card or try to pick one up for under $100 (not quite the Radeon HD 5770 or 5870 that would have originally come with it). I also do not have an Apple keyboard or mouse and I assume I can simply attach a generic PC USB keyboard and mouse? That's another reason I want to run Ubuntu on it rather than buy OS X.

---

### Post by luciano.x on 2015-08-26
Check [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) and [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) for supported GPUs.
You can always try a live cd to test sound and other peripherals.

A generic kb and mouse is fine.
Some early mac versions work only with linux 32bits (fixme).

---

### Post by HDTimeshifter on 2015-09-02
I just got done refurbishing a Pentium D PC using an old VisionTek X1550 (ATI Radeon X1550 GPU) card that's not on the Radeon driver list above, but it worked, then pulled that and inserted it in the Mac Pro. I also formatted and tested a 500 GB hard drive in that Pentium D system and stuck it in the Mac Pro. Then I created a bootable Ubuntu 14.0.4 LTS USB and inserted it in the Mac Pro (can't boot from live CD since there is no way to open the Superdrive before boot - back in the old days of original Mac & Mac II they used to have a pin hole that you could manually eject with a paper clip, I didn't see one), and tried to boot. The monitor light never goes from orange to green, even though the Mac power light goes blue and I can hear the fans and HD spinning and a USB mouse lights up. There is some discussion on the Apple site about non-EFI video card support, but I think that has to do with OS X and not Ubuntu. I don't really want to buy a used Apple firmware video card (ATI Radeon HD 5770) for $250 that might not even work either. Any suggestions?

---

