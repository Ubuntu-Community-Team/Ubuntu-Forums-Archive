---
title: "iMac G3 Question"
date: 2007-06-25
forum: Apple PPC Users
---

### Post by DoctorDemento on 2007-06-25
I am new to Mac but not Ubuntu. I have been given an iMac G3 w/266MHz PPC, 160MB RAM, 6GB harddrive and OS 8.5.1. I have read the PPC FAQ but I am confused. Is this G3 a 'old world' or 'new world'? Also, is it possible to run the live CD, the FAQ only states that you need 256MB to install from a live CD.

---

### Post by pxwpxw on 2007-06-25
The iMacG3 must be OldWorld if it is running on 8.5 - I would think.

Easy way to confirm that is to download BootX 1.2.b3 from the last link on my rough  [ [COLOR="Red"]Old World Notes[/COLOR] ]("http://ubuntuforums.org/showpost.php?p=2746588&postcount=3")

 and see if you can unpack the .sit file
and install/run BootX application and extension (you will need both to install and run ubuntu on oldworld). Certainly dont try to use the Desktop (live) CD for install, and very very slow to run as stan dalone. You will need the ALternate or Server cd iso to install.

You will need the macos8.5 install CD to partition the disk before installing.

Edit: Its definitely New World. My education continues.

---

### Post by 3rdalbum on 2007-06-25
All Macs from the iMac (which was released in 1998) onwards are New-world.

I don't know if the Ubuntu Live CD will run, but Xubuntu definately will even with that low amount of RAM. You can try it - it won't hurt your computer. Put in the CD and hold down the C key while starting up or restarting and the CD will boot.

If you've been given that computer, I'd assume you don't want to run Mac OS 8.5 on it. Since it's a New-world machine, you can just let the Ubuntu installer blow away your existing partitions, and so you don't need the Mac OS CD.  If you want to keep the Mac OS on there, you should use the Mac OS CD to erase the hard disk, partition it so that there's "unallocated" space for Ubuntu, reinstall Mac OS and then install Ubuntu into the unallocated space.

---

### Post by pxwpxw on 2007-06-25
3rdalbum

I thought iMacs were New world also, but at the same time I thought 8,5 would not run on a NewWorld mac?

---

### Post by 3rdalbum on 2007-06-25
I think 8.1 works with the first iMacs; I may be wrong about this. My Rev C iMac came with 8.5.

It's such a great coincidence that Apple changed the case styling, the connectivity ports and the firmware version at the same time. So basically, if the case isn't beige, it's a New-World. If it shipped with USB ports, it can run OS X. Like a mnemonic :-)

---

### Post by pxwpxw on 2007-06-25
Thanks, I remember when I got a pmac7300 with 8.5, the first iMacs came out and  8.5 was current then 1998 I think. Just now I tried the 8.5 disk on an iBookG4, could be installed with classic support in macosx, but I declined.

---

### Post by DoctorDemento on 2007-06-25
Thank you for your responses. Before I got any replies, I was able to download the live iso and burn the image. That little old tangerine iMac was able to run it, albeit excruciatingly slow. Unfortunately the iMac did not come with any OS discs so I am stuck with it, locked into a limited user login, or so it seems (maybe someone can shed some light on this?). Rather than wipe the original hdd I was thinking about putting in another hdd and installing Linux on it. It was mentioned that the Xubuntu live CD would run better. Would Xubuntu run better as a desktop install also?

---

### Post by pxwpxw on 2007-06-26
Re your points:

Any Live desktop CD will be very slow on that system, painfull I would say.

But an installed system would be fine. I would suggest xubuntu appropriate.
But use the Alternate install cd.

Limited login? maybe you need < sudo su > if you refer to ubuntu live.

You can re-size your macos partition from ubuntu install, if you want a compromise solutiion.

Here 2 links I just found, all about the original imacs, for light reading.

The iMac Family of Computers
[http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/iMac_26Oct99/iMac.pdf](http://developer.apple.com/documentation/Hardware/Developer_Notes/Macintosh_CPUs-G3/iMac_26Oct99/iMac.pdf)
=================

iMac G3 (Original) User Manual
[http://manuals.info.apple.com/en/iMacG3_originalUserManual.PDF](http://manuals.info.apple.com/en/iMacG3_originalUserManual.PDF)
=================

---

### Post by 3rdalbum on 2007-06-26
> **DoctorDemento said:**
> Rather than wipe the original hdd I was thinking about putting in another hdd and installing Linux on it.

If you do that, I think it will have to be a replacement for the original hard disk; iMacs weren't built with hardware expandability in mind. Alternatively, you could try finding some second-hand Mac OS 8.5 or Mac OS 9 discs, as long as they actual Mac OS install discs and not just specifically for a particular Mac model.

---

### Post by DoctorDemento on 2007-06-26
Success! First, I had an old Western Digital 8GB hdd laying around from an old XBox console. I unlocked it, wiped it, and installed it. Next I installed Xubuntu 6.06 from the alternate CD with no trouble. Last, I installed the Gnome desktop, just to see if there was noticable performance hit. While both GUI's worked flawlessly, Xfce was obviously faster so I will probably stick with it. Thank you to everyone who helped on this post, but I'm sure I'll be back with more questions as I can already see some teething issues. For example the screen is to the right a bit, leaving a 1/4" black margin on the left.

3rdalbum wrote:
> If you do that, I think it will have to be a replacement for the original hard disk; iMacs weren't built with hardware expandability in mind.

Actually, the iMac will except any standard 5400rpm ATA/Ultra ATA IDE hdd. While there might be a limit on the logical size, MacWorld stated that they installed a 60GB without concern.

BTW, I wrote this reply from the iMac! ;)

---

### Post by 3rdalbum on 2007-06-27
> **DoctorDemento said:**
> 
Actually, the iMac will except any standard 5400rpm ATA/Ultra ATA IDE hdd. While there might be a limit on the logical size, MacWorld stated that they installed a 60GB without concern.

BTW, I wrote this reply from the iMac! ;)

Good stuff! I actually meant that you can't add a second internal hard drive - that you'd have to take the original out first. I'm not entirely sure on that, so if you've got two hard drives in there I congratulate you :-)

Ubuntu is great on the PowerPCs now, so I'm sure you'll have a fun and productive time!

---

### Post by DoctorDemento on 2007-06-27
Okay, I understand what you were thinking now. I can't speak for the second gen iMac G3's but there is no way to fit a second hdd in the first gens without some serious butchering. Also I am not sure if the IDE interface is setup for more than one.

---

### Post by bodycoach2 on 2007-06-27
On older iMacs (under 500 MHz), I'd recommend sticking with Xubuntu. I've installend Xubuntu 6.06.1 on several iMacs now, and upgraded/updated them all from there. I also recommend sticking with the original hard drive, and using an external USB hard drive for more storage. Doing it that way, you're not limited by the hardware of the iMac. I regularly use a 250 GB USB hard drive with a iMac 333 Mhz, 160 mb ram, 8 GB hard drive, Xubuntu 7.04 installed. 

Now, if I can just find a usb wireless solution for them!

Also, you can find really good deals on older iMacs on Publicsurplus.com

---

### Post by DoctorDemento on 2007-06-28
That really is a great site, but nothing is in my area and everything seems to be local pick-up. I'll bookmark it for future reference though. ;)

---

### Post by pandan on 2008-01-30
hey there,

did you fix the black line at the edge of your screen?

I think you can lookup solutions that use the xvidtune command and paste the output setup into
your xorg.conf.

Phil

---

### Post by Ripfox on 2008-01-30
Am I wrong, or do all G3s have broken video playback with anything after 6.10?

---

### Post by oswaldkelso on 2008-01-30
> **DoctorDemento said:**
> Success! First, I had an old Western Digital 8GB hdd laying around from an old XBox console. I unlocked it, wiped it, and installed it. Next I installed Xubuntu 6.06 from the alternate CD with no trouble. Last, I installed the Gnome desktop, just to see if there was noticable performance hit. While both GUI's worked flawlessly, Xfce was obviously faster so I will probably stick with it. Thank you to everyone who helped on this post, but I'm sure I'll be back with more questions as I can already see some teething issues. For example the screen is to the right a bit, leaving a 1/4" black margin on the left.

3rdalbum wrote:


Actually, the iMac will except any standard 5400rpm ATA/Ultra ATA IDE hdd. While there might be a limit on the logical size, MacWorld stated that they installed a 60GB without concern.

BTW, I wrote this reply from the iMac! ;)

You can run larger than 8gb hds in tray loading imacs but the root partition must contain the os. see this thread for more details. 

[http://ubuntuforums.org/showthread.php?t=605522&page=2](http://ubuntuforums.org/showthread.php?t=605522&page=2)

---

