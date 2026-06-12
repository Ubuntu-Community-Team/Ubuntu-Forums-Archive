---
title: "I have a laptop that I'm installing Ubuntu on and need some advice..."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-11
I got a laptop (has Vista on it now) and I'm trying to figure out if Ubuntu would run well on it.  I'm going to wipe the entire drive to rid all traces of Vista on it, but is it sort of easy getting wifi working or no?  Also, recommend a Ubuntu distro for me if you don't mind and would Arch be a good way to go, is it as hard as gentoo to compile or easier?

Laptop Specs:

2ghz AMD 64 Turion Mobile
1gb RAM
nvidia geforce go 6150
broadcom 802.11g WLAN
nvidia nforce networking controller
SDA standard complaint SD host controller
100gb hdd

The laptop also has some buttons above the keyboard for rewind, fastforward, play, stop, etc.  Would those be hard to get working in Ubuntu?  Also, it has a SD card reader built in, so I would need that to work as well.  I think I listed everything I needed to, so tell me how hard it would be to get a working Ubuntu on this laptop and which Ubuntu I should go with.

---

### Post by notwen on 2007-09-11
Is there a specific make/model of your laptop?  It's easier to look for other people's experience with a specific laptop rather than looking up people's experience with specific hardware.  That being said, your graphics chipset should work well being an Nvidia and generally people tend to have lots of issues w/ Broadcom wireless.

---

### Post by Luinar on 2007-09-11
Ubuntu will run fine with the specs you listed. As to which version of Ubuntu to go for, the best advice I can give is to try them all out and see what you prefer since in the end it is all down to personal preference. Either grab live discs for X/K/Ubuntu, or if you wish  install Ubuntu and then install XFCE and KDE through Synaptic. You will then be able to select which Desktop Environment you want to use at the login screen. Once you've found the one you like, the others can be removed, should you so desire.

As for the wi-fi, it should be possible to get working if not out of the box then by loading the Windows driver using ndiswrapper - this is what I had to do on my laptop and it worked fine, but as with everything mileage may vary between different hardware.

Also, the rewind/forward/etc. keys and the SD card reader could pose some problems as, in my experience, it is often these 'specialist' features which can cause the most hassle. Then again, they may work, or it might be possible to get them working, but you should at least prepare yourself for some tinkering and realise that it may not always be possible to get 100% functionality.

---

### Post by zetsumei on 2007-09-11
It's a newer laptop, so I didn't think anyone would of had experience with it yet, but it's an HP Pavilion dv6000

> **Luinar said:**
> Ubuntu will run fine with the specs you listed. As to which version of Ubuntu to go for, the best advice I can give is to try them all out and see what you prefer since in the end it is all down to personal preference. Either grab live discs for X/K/Ubuntu, or if you wish  install Ubuntu and then install XFCE and KDE through Synaptic. You will then be able to select which Desktop Environment you want to use at the login screen. Once you've found the one you like, the others can be removed, should you so desire.

As for the wi-fi, it should be possible to get working if not out of the box then by loading the Windows driver using ndiswrapper - this is what I had to do on my laptop and it worked fine, but as with everything mileage may vary between different hardware.

Also, the rewind/forward/etc. keys and the SD card reader could pose some problems as, in my experience, it is often these 'specialist' features which can cause the most hassle. Then again, they may work, or it might be possible to get them working, but you should at least prepare yourself for some tinkering and realise that it may not always be possible to get 100% functionality.

It would be nice to get the SD card reader and the keys working, but at most I want it for internet wifi, and some school apps, like OO.org.

---

### Post by stchman on 2007-09-11
> **zetsumei said:**
> I got a laptop (has Vista on it now) and I'm trying to figure out if Ubuntu would run well on it.  I'm going to wipe the entire drive to rid all traces of Vista on it, but is it sort of easy getting wifi working or no?  Also, recommend a Ubuntu distro for me if you don't mind and would Arch be a good way to go, is it as hard as gentoo to compile or easier?

Laptop Specs:

2ghz AMD 64 Turion Mobile
1gb RAM
nvidia geforce go 6150
broadcom 802.11g WLAN
nvidia nforce networking controller
SDA standard complaint SD host controller
100gb hdd

The laptop also has some buttons above the keyboard for rewind, fastforward, play, stop, etc.  Would those be hard to get working in Ubuntu?  Also, it has a SD card reader built in, so I would need that to work as well.  I think I listed everything I needed to, so tell me how hard it would be to get a working Ubuntu on this laptop and which Ubuntu I should go with.

Download the Feisty LiveCD and give it test drive.  The Broadcom card is not natively supported by Linux but there are numerous methods to getting that card working.

---

### Post by overdrank on 2007-09-11
> **zetsumei said:**
> It's a newer laptop, so I didn't think anyone would of had experience with it yet, but it's an HP Pavilion dv6000



It would be nice to get the SD card reader and the keys working, but at most I want it for internet wifi, and some school apps, like OO.org.

Hi a quick search turns up 
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
[http://ubuntuforums.org/showthread.php?t=515386&highlight=HP+Pavilion+dv6000](http://ubuntuforums.org/showthread.php?t=515386&highlight=HP+Pavilion+dv6000)
Just to name a few and it does look promising. :)

---

### Post by zetsumei on 2007-09-11
I have fiesty already on CD, but is there two ISO's, one for the livecd and one for the install?  Isn't the installer on the livecd, I think thats the one I got.

---

### Post by Beowulf.1000 on 2007-09-11
I always seem to have Broadcom wifi on my laptops, and ultimately went with linuxant.com proprietary driver that lets you use your Windows wifi driver with linux. So copy or download your Vista drivers for your wifi somewhere, then pay the $20 for linuxant driver (you can download and try it 30 days free to be sure it works before paying) and you are usually good to go. Has worked for many several times. You pay a little, but pretty easy to get up and runnuing. O/w you can always use a pcmcia card, such as DYNEX or other pcmcia that uses atheros chipset, and install madwifi package for atheros wifi.

> **zetsumei said:**
> I got a laptop (has Vista on it now) and I'm trying to figure out if Ubuntu would run well on it.  I'm going to wipe the entire drive to rid all traces of Vista on it, but is it sort of easy getting wifi working or no?  Also, recommend a Ubuntu distro for me if you don't mind and would Arch be a good way to go, is it as hard as gentoo to compile or easier?
...
broadcom 802.11g WLAN.

---

### Post by notwen on 2007-09-11
> **zetsumei said:**
> I have fiesty already on CD, but is there two ISO's, one for the livecd and one for the install?  Isn't the installer on the livecd, I think thats the one I got.

The LiveCD will bring you into a Live environment, Ubuntu is running w/o actually touching your system's HDD.  From there you can choose to install simply by double-clicking on the "Install" icon on your desktop.

---

### Post by zetsumei on 2007-09-11
I'll play with it tonight, got class now.  Thanks for the answers and those threads.  Looks like I might use the 32bit cd instead.

---

### Post by zetsumei on 2007-09-11
-_-

I booted fine into the 32bit 6.10 ubuntu cd, but my mouse, etc. aren't working.  Mouse is the touchpad.  Is there someway to enable it to be used in the livecd.  Also, when I was booting it, there was only 2 OK's on the screen before it went to Ubuntu.  Is that bad, or what?

---

