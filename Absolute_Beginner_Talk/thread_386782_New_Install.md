---
title: "New Install"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by tbuss on 2007-03-17
I've done some research and I have received some excellent feedback from other members on making the switch to Ubuntu. 

[http://www.ubuntuforums.org/showthread.php?t=385932](http://www.ubuntuforums.org/showthread.php?t=385932)

I'm in school right now so there are some things I absolutely need windows for. I looked at dual booting the OS's but the various forums and sites i visited had, at times,  useful but conflicting information. It is hard to choose which is the best option. I found a HowTo in a Installation thread here but it was for a different version of Ubuntu. [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
I visited the X chat #Ubuntu session and received plenty of help on hardware compatibility and other issues. Everything seems like a go, I just need both operating systems right now.

What I thought I could do was leave my current windows partitions as is, and install Ubuntu on my Maxtor One Touch II external HDD. My computer has two internal hard drives that I want to be unaffected by the install. Instead I would just like to install Ubuntu on the external drive and dual boot that way if possible. My external drive connects via firewire, a lot of info I have found is for drives that connect via usb. Does anyone have any ideas on how I might be able to accomplish this?

---

### Post by dstew on 2007-03-17
If you want to leave your Windows disk and partitions absolutely untouched, you will have to have some way to boot your Ubuntu Linux after you install it. The Windows XP booter cannot do that. One way is to change the boot order and put the firewire disk first, but most BIOSes I think cannot boot a firewire drive. The other way is to make a boot floppy with grub on it, and boot from there.

Really, the best way to do it is to install Ubuntu on the external drive, and let grub configure itself to dual-boot. You do not have to be afraid of having grub installed on the master boot record of your windows disk.

Here is a how-to about installing Linux on an external firewire device. It really all depends on whether or not your BIOS recognizes the firewire disk. If it does, you should have no problem installing:

[http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html)

---

