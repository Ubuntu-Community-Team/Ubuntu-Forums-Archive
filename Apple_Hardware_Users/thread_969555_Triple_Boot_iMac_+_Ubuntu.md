---
title: "Triple Boot iMac + Ubuntu"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by claudius753 on 2008-11-03
Ok, just for quick background information, after buying an iPhone last year, I realize how much I would really use a portable machine (notebook or netbook). The Apple portable products are ridiculously overpriced imho, $1500 for integrated graphics or $2000 for the cheapest 15".

That means I will be buying a "PC" (not that a Mac isn't a PC) notebook or netbook (MSI Wind/Eee PC/Mini 9/Mini 100 etc). I don't want to use Windows as my only OS, so I will be installing Linux on anything I would buy.


Before I buy anything, I want to see how far Linux has come in the 4 years since I started using Mac OS X. So, I want to install it on my 1+ year old iMac currently with 2 partitions, one OS X and one Vista.

I have the Ubuntu 8.04 Hardy 64 bit CD. The CD runs Live decently, though no wifi. I can't get the install to work though. It goes through the install fine, but when I'm done I can't get it to boot. I originally tried this using rEFIt. When the system turns on, and I get a logo of an hd with the finder logo (to boot OS X) and I get a logo with an hd and the penguin (for linux), so it does recognize that linux is there and installed. When I choose linux, the screen goes black and then nothing happens.

I am pretty sure that I didn't put the boot loader in the right place. I don't know where I should install grub. Macs apparently don't have MBRs like normal hard drives?

Also, I have read that there are problems with the 64 bit editions of Linux and there are no real performance gains, so the 32 bit is preferable? Especially to get the Broadcom wifi card in the Mac to work with 64 bit. I'm about to go to work, so I may just download Intrepid 32 bit while I'm gone to try tonight.

It's been a while since I've used linux, so I guess I'm a newbie again, so thanks for any help.

---

### Post by cyberdork33 on 2008-11-03
> **claudius753 said:**
> I have the Ubuntu 8.04 Hardy 64 bit CD. The CD runs Live decently, though no wifi.
You can probably get it working if you 'sudo rmmod b43, sudo rmmod ssb, sudo modprobe wl'
> **claudius753 said:**
> I can't get the install to work though. It goes through the install fine, but when I'm done I can't get it to boot. I originally tried this using rEFIt. When the system turns on, and I get a logo of an hd with the finder logo (to boot OS X) and I get a logo with an hd and the penguin (for linux), so it does recognize that linux is there and installed. When I choose linux, the screen goes black and then nothing happens.use the partition tool in the rEFIt menu to sync the partitions
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

> **claudius753 said:**
> I am pretty sure that I didn't put the boot loader in the right place. I don't know where I should install grub. Macs apparently don't have MBRs like normal hard drives?doesn't matter to make it work, but it does if you want to be able to start Ubuntu, Windows, and OS X all straight from the rEFIt menu.

> **claudius753 said:**
> Also, I have read that there are problems with the 64 bit editions of Linux and there are no real performance gains, so the 32 bit is preferable? Especially to get the Broadcom wifi card in the Mac to work with 64 bit. I'm about to go to work, so I may just download Intrepid 32 bit while I'm gone to try tonight. There are pros and cons, but they are all but negligible now. I have been using 64bit for years with little issue at all. You really only NEED 64bit if you have more than 3GB of RAM...

Advantages and Disadvantages:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by claudius753 on 2008-11-05
Hmm, interesting about the 64 bit vs 32 bit.  I have gotten 8.10 installed and working using the 32 bit version, but I do have 4 GB of ram, and indeed only 2.9 gb is showing up.  I might try to see if I can get the 8.04 Hardy 64 bit live version running with wifi, and if I can, I might install that instead and the update to 8.10.  

I can update from 8.04 to 8.10 through the update manager, right?

---

### Post by cyberdork33 on 2008-11-05
> **claudius753 said:**
> Hmm, interesting about the 64 bit vs 32 bit.  I have gotten 8.10 installed and working using the 32 bit version, but I do have 4 GB of ram, and indeed only 2.9 gb is showing up.  I might try to see if I can get the 8.04 Hardy 64 bit live version running with wifi, and if I can, I might install that instead and the update to 8.10.  

I can update from 8.04 to 8.10 through the update manager, right?
I wouldn't recommend that as upgrades tend to go bad, but yes, theoretically you can.

We can get your wifi working in either 32bit or 64bit.

---

### Post by claudius753 on 2008-11-05
Ok, I booted the 64 bit 8.04 Hardy, and tried your instructions but they did not work, I got errors.

So, I tried to compile the Broadcom drivers and used insmod and it seems to be working now (I'm posting from the live cd over wireless internet)

I was going to install hardy 64 bit, then update to intrepid...Are you saying that it is a better idea to just download Intrepid and install from that because updating from one version to the next versions cause problems?

I don't really see a speed difference from the 32 bit to the 64 bit, but it is recognizing the full 4 GiB of ram, so 64 bit it is I guess.

---

### Post by cyberdork33 on 2008-11-05
> **claudius753 said:**
> So, I tried to compile the Broadcom drivers and used insmod and it seems to be working now (I'm posting from the live cd over wireless internet)

I was going to install hardy 64 bit, then update to intrepid...Are you saying that it is a better idea to just download Intrepid and install from that because updating from one version to the next versions cause problems?
Yes, plus Intrepid has the new broadcom driver that is a bit easier to use.

What driver did you "compile"?

---

### Post by claudius753 on 2008-11-05
I compiled the 64 bit driver from broadcom's website.

I went ahead and downloaded and installed 64 bit intrepid, but now I have more issues.  I have wireless working, and all 4 GB of ram is available, but now I have absolutely no sound whatsoever.  

I'm starting to rethink buying a netbook and installing ubuntu, I don't know if these are just issues related to apple hardware or if I'd have this much trouble on a netbook.  I don't seem to remember this many problems back when I last experimented with linux

---

### Post by cyberdork33 on 2008-11-05
> **claudius753 said:**
> I compiled the 64 bit driver from broadcom's website.

I went ahead and downloaded and installed 64 bit intrepid, but now I have more issues.  I have wireless working, and all 4 GB of ram is available, but now I have absolutely no sound whatsoever.  

I'm starting to rethink buying a netbook and installing ubuntu, I don't know if these are just issues related to apple hardware or if I'd have this much trouble on a netbook.  I don't seem to remember this many problems back when I last experimented with linux
well, as I said, many of the issues of Hardy (the MacBookPro4,1 was still new) are not a problem in Intrepid. (That driver you "compiled" is already in Ubuntu in Intrepid)

---

### Post by claudius753 on 2008-11-05
I did go back and use Intrepid and am using it's built in drivers.  The driver from broadcom that I "compiled" (or made or built or whatever you would call it) was used under Hardy, I'm not using it now.

However, sound worked in 32 bit Intrepid but in 64 bit Intrepid it does not work.  Trading one problem for another...

---

### Post by cyberdork33 on 2008-11-05
> **claudius753 said:**
> However, sound worked in 32 bit Intrepid but in 64 bit Intrepid it does not work.  Trading one problem for another...
OK, run 'alsamixer' in a terminal and make sure that the channels are unmuted and turned up.

---

### Post by claudius753 on 2008-11-05
> **cyberdork33 said:**
> OK, run 'alsamixer' in a terminal and make sure that the channels are unmuted and turned up.

That would be the first thing I tried :)  I also installed the gui tools (GNOME ALSA Mixer and alsamixergui) just to make sure, nothing worked.

On searching, it appears that many people are having issues with this particular chip, not just on Macs either.

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Apple Computer Inc. Device 00a0
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at d0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

