---
title: "building a new computer..."
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by hairmetal4ever on 2006-12-26
I am looking to build a new PC.  Probably an Intel Core 2.  Are there any issues I need to keep in mind with Linux compatibility?

Also, I will be dual-booting.  1-I'm still not too well-versed in Ubuntu and 2-my fiance NEVER will be, so Windows will stick around.  Plus, I work from home some and require some proprietary software not available for Linux.

Anyway, are there any suggestions and recommendations for hardware?

Also, I plan on installing two hard drives, one for Linux of about 750GB, that will be formatted as one FAT32 partition of about 550 GB to share data between the two OS's, the other for the Ubuntu OS and Linux-only program installations.  The other HDD will probably be a windows-only 250 gig or so.

Should I go with SATA drives?

---

### Post by Ocxic on 2006-12-26
Sata prvodes faster transfer rates, it really doesn't matter if you use IDER orSATA, but I would go with SATA just cause it's newwer and will prolly replace IDE

---

### Post by PriceChild on 2006-12-26
Depending on where you're buying from, see if you can take a Live CD along to test out ubuntu to check out the compatability.

BTW that's 3 very good reasons for you not to be switching to linux...

---

### Post by scrooge_74 on 2006-12-26
Try to find Linux compatible parts so you can save on headaches latter on

---

### Post by BarfBag on 2006-12-26
Get an nVidia graphics card.  Their drivers are a lot better (in both Windows and Linux).

---

### Post by elcasey on 2006-12-26
I started a similar thread on another (hardware-related) forum. I first installed Linux on a Pentium90 back in 1998 and the hardware issues were insane. I didn't mess with it for a long time after that, for that very reason.

Today, however, it seems almost everything is Linux compatible. The Core2 Duo boards all seem to be generally Linux-compatible. I'm looking at putting together a new box myself soon, with a Foxconn board, an E6300 proc and probably a 7600-series GeForce videocard. As far as I know, the onboard stuff (especially the Foxconn, which is a barebones board) is all compatible with Linux, with the possible exception of some sound "weirdness." Creative Labs sound hardware usually works with Linux.

SATA should work fine, eSATA works, I don't think you'll have any difficulties on the HDD or optical drive front. 

Are you going to be building this machine yourself or buying a pre-built rig?

---

### Post by tarpon_bill on 2006-12-26
Might want to make sure the CPU and chipset support virtualization.

---

### Post by hairmetal4ever on 2006-12-26
> **PriceChild said:**
> Depending on where you're buying from, see if you can take a Live CD along to test out ubuntu to check out the compatability.

BTW that's 3 very good reasons for you not to be switching to linux...

Well, I like it so far, and since it's free, it can't hurt!  I will use it almost exclusively for my non-work activities.  Might have to switch back to windows when I'm working.  And I'm working on the fiance.

---

### Post by hairmetal4ever on 2006-12-26
> **elcasey said:**
> I started a similar thread on another (hardware-related) forum. I first installed Linux on a Pentium90 back in 1998 and the hardware issues were insane. I didn't mess with it for a long time after that, for that very reason.

Today, however, it seems almost everything is Linux compatible. The Core2 Duo boards all seem to be generally Linux-compatible. I'm looking at putting together a new box myself soon, with a Foxconn board, an E6300 proc and probably a 7600-series GeForce videocard. As far as I know, the onboard stuff (especially the Foxconn, which is a barebones board) is all compatible with Linux, with the possible exception of some sound "weirdness." Creative Labs sound hardware usually works with Linux.

SATA should work fine, eSATA works, I don't think you'll have any difficulties on the HDD or optical drive front. 

Are you going to be building this machine yourself or buying a pre-built rig?

Buying a prebuilt barebones w/case, CPU, motherboard, and RAM from an ebay dealer and then buying and installing my own drives, video card, etc.

---

### Post by hairmetal4ever on 2006-12-26
> **tarpon_bill said:**
> Might want to make sure the CPU and chipset support virtualization.

CPU is going to be Intel Core 2 Duo E6600 2.4 Mhz.  Motherboard probably a ASUS P5B P965.  How do I find out if they support virtualization (which is WHAT exactly?)

---

### Post by smoker on 2006-12-26
you might be well to have a practice with ubuntu in your present machine, and for your new pc there is a list here that may help:

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---

### Post by lyceum on 2006-12-26
> **hairmetal4ever said:**
> CPU is going to be Intel Core 2 Duo E6600 2.4 Mhz.  Motherboard probably a ASUS P5B P965.  How do I find out if they support virtualization (which is WHAT exactly?)

Virtualization, so one can/will correct me if I am wrong, is when you run one OS on top of another OS, so running Windows **in** Ubuntu, for example. I was actually going to suggest that when I read your post. If you can get that going, you might only need one hard drive. As for the shopping, go to a shop, look for the penguin. Take notes, go back to e-bay.

---

### Post by elcasey on 2006-12-26
VMWare is the big name in virtualization. The best example right now is probably the Parallels Desktop software for Intel Macs. You don't have to run a dual-boot of OSX and WinXP, you simply invoke Parallels with a hotkey and *boom* you're in Windows (inside of OSX).

You can do the same with Linux on PPCs and Intel Macs running MacOnLinux, and eventually you will be able to run Windows Vista on OSX the same way that Parallels runs XP now. You can run virtual images for other distros on Linux, you can run images of some of the BeOS clones (I'm probably the only one here that really misses Be)...

To put it mildly, it's damned cool stuff! But I haven't messed with it much at all. I would imagine any of the more modern boards and processors (which would include anything and everything Core2Duo) will support virtualization.

---

### Post by PriceChild on 2006-12-26
> **PriceChild said:**
> BTW that's 3 very good reasons for you not to be switching to linux...Because you can't use it for work, your partner won't want to use it & the fact that there are proprietary apps which you can't replace under linux.

---

### Post by hairmetal4ever on 2006-12-27
> **elcasey said:**
> VMWare is the big name in virtualization. The best example right now is probably the Parallels Desktop software for Intel Macs. You don't have to run a dual-boot of OSX and WinXP, you simply invoke Parallels with a hotkey and *boom* you're in Windows (inside of OSX).

You can do the same with Linux on PPCs and Intel Macs running MacOnLinux, and eventually you will be able to run Windows Vista on OSX the same way that Parallels runs XP now. You can run virtual images for other distros on Linux, you can run images of some of the BeOS clones (I'm probably the only one here that really misses Be)...

To put it mildly, it's damned cool stuff! But I haven't messed with it much at all. I would imagine any of the more modern boards and processors (which would include anything and everything Core2Duo) will support virtualization.

Looks like the board I picked DOES support virtualization.

Question - how does this differ from something like WINE?

---

### Post by lyceum on 2006-12-28
> **hairmetal4ever said:**
> Looks like the board I picked DOES support virtualization.

Question - how does this differ from something like WINE?

Yes. Wine (as I understand it) creates a "fake" C:// for your windows apps to run. (This is a crappy way of putting it, but you should get the point). So your Windows apps run off a C drive, like they should, even though it is not really there. Because of this, WINE does **not **work with everything. 

Vertualization IS Windows. So you boot Ubuntu, then you boot Windows, letting it run INSIDE Ubuntu. No need to dual boot, and all the MS programs will work, as you are running them from Windows. (How cool is that?)

So, you can have your cake and eat it too. 8)

---

