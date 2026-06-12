---
title: "easiest method for single boot Ubuntu on mac mini (late 2009)?"
date: 2016-01-19
forum: Apple Hardware Users
---

### Post by DiGiTY on 2016-01-19
I want to install and single boot Ubuntu (completely replacing Msc OS X) on a Mac Mini late 2009. What's the easiest method?

---

### Post by BobUgh on 2016-01-20
Before wiping out OSX, check that you have latest firmware, [https://support.apple.com/en-us/HT201518](https://support.apple.com/en-us/HT201518)  And if you don't have the original osx install discs or snow leopard install DVD, consider cloning the current internal drive to a usb drive so you can boot into osx in the future if the need ever comes up.

From the target machine, using your internet browser, get the standard 14.? LTS .iso download, it will have amd64 or something like that in the name. From what I have been told you shouldn't need the special one that has "mac" in the name unless your mac is one of the few that requires it; I have been told your browser silently reports your mac model to canonical and their website selects the correct iso for you. AFAIK the differences in the .iso files are for booting the live DVD; the installation bits are the same. Burn the DVD from that iso, it may not matter what machine you use to do the burn. Then boot from it holding "C" key down while powering on.

If you already have a 14.n LTS live install media, just try it. If it is usb, hold the "option" key down while booting.

---

### Post by DiGiTY on 2016-01-21
Oh, that's it?!! It's a straight up standard install?!! Is rEFIt or rEFInd (or whatever EFI/BIOS workaround) no longer required to install Ubuntu?

---

### Post by BobUgh on 2016-01-22
If you don't want multi-boot, it can be a standard install. You might get a long boot time, if so come back here and start a new thread about blessing?

My long version:
I don't advise the following, I am just stating some information from "experimentation". A few months ago, I cloned a multi boot disk (Ubuntu, Vista) from an **old** Acer laptop onto a new SSD, stuck it into a Dell laptop, and it booted into Grub and then Ubuntu fine - from Grub if choose Vista, it quickly failed. Then sometime later I installed that same SSD into a newer mac book pro; My intention was to wipe the whole drive and make a clean install of OSX. But just before I did that, on a whim, I decided to see what would happen if I simply powered on. After a long pause, it booted into Grub then Ubuntu fine! I tried terminal, it seemed functional. I quickly shut down since I had no intention of using Ubuntu on that machine. Keep in mind that SSD was MBR (not GPT) and the install was done on that old Acer circa 2010.

So I don't understand all the stuff about EFI/BIOS&#8230; It is my impression you need to be concerned about that only for multi boot. But it may have something to do with the long pause before booting.

I thought the long pause before booting is because the Mac Startup Manager keeps looking for a blessed partition or file for 30 seconds before doing a legacy boot. You just need to bless it, but I don't understand how I can bless it from OSX when OSX won't mount the ext4 partition&#8230; I have since moved on to other systems, and for a single boot system on a Mac, I either had a long boot time, OR: I was able to hold "option" key down while booting, select the one system it gave me, click boot, and that was faster!

---

### Post by DiGiTY on 2016-01-26
Got Ubuntu installed, but the Ethernet and wireless (airport) card aren't detected. How do I at least install the drivers for the wireless card via command line for Ubuntu Server (the machine doesn't have Internet access obviously)?

---

