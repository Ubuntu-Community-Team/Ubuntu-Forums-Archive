---
title: "Question regarding Ubuntu and Shuttle's new kpc Linux computer"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by norfair on 2008-03-31
I was thinking about ordering one of Shuttle's new kpc computers, but wondered how easy it would be to get Ubuntu on it. It ships without an operating system installed (I think), as it includes a flash drive containing it. The operating system Shuttle has gone with is Foresight Linux. It doesn't appeal to me, as I've long been an admirer of Ubuntu and know nothing of Foresight Linux. So, how difficult would it be if I ordered the system with the notion of never installing Foresight Linux and instead installing Ubuntu? The catch is that this "simple PC" doesn't feature a DVD/CD drive. I'd get an external one for later, but could I download Ubuntu, pop it on an SD card and then that into an SD card reader/flash drive and install Ubuntu that way? On a related matter, are all external DVD/CD drives Ubuntu/Linux compatible? Thanks!

For reference, here is what I am considering:
[http://us.shuttle.com/kpc/buy.html](http://us.shuttle.com/kpc/buy.html)

It would be the SLK-4500 model. Most likely with the basic Pentium processor, 2GB RAM, 250GB HD, and I'd get the external DVD/CD drive from NewEgg. I already have a monitor, and would get a Ubuntu keyboard from ZaReason. The system itself from Shuttle would cost around $329. I'd reeeeaaaally rather order from ZaReason, but I'm feeling cheap at the moment and can't seem to get my ZaReason order under $600. Plus, I like the fact that Shuttle's kpc is so energy efficient and has the option of adding your own pictures on the front (however silly that may be for choosing a computer). If anyone feels like offering up their opinion on my reasoning and option, I'd appreciate it.

---

### Post by ugm6hr on 2008-03-31
If you have ethernet broadband, the easiest way to install Ubuntu...

Create partitions with GParted (hopefully you can get that with the included Linux distro).

Use UnetBootin to install: [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by norfair on 2008-03-31
Thanks for the suggestion, ugm6hr. However, that might be my last resort. The condition of my current PC wouldn't allow for such a feat, and I don't want to have to install the OS included with the PC I plan on getting. 

I wonder, though. If I ordered a Live CD from Ubuntu or created my own and bought an external DVD/CD drive, could I hook it up to the new PC, pop in the CD, and have it work? Does that make sense? I don't know if external DVD/CD drives need to be configured first, or if they are plug and play and would thereby allow for the PC to load straight from the CD. 

Any suggestions?

---

### Post by Syke on 2008-04-01
Hi norfair,

ZaReason has a KPC in the shop and is considering offering it with Ubuntu preloaded.

It is pretty fun to customize the front with your own graphics.

---

### Post by ugm6hr on 2008-04-02
> **norfair said:**
> The condition of my current PC wouldn't allow for such a feat, and I don't want to have to install the OS included with the PC I plan on getting. 

Is the new PC not pre-installed with Foresight Linux?  Sorry, I misunderstood then.

> I wonder, though. If I ordered a Live CD from Ubuntu or created my own and bought an external DVD/CD drive, could I hook it up to the new PC, pop in the CD, and have it work? Does that make sense? I don't know if external DVD/CD drives need to be configured first, or if they are plug and play and would thereby allow for the PC to load straight from the CD.

Hmmm... depends on whether an external USB drive is recognised by BIOS or not.  Don't know the answer to that one.

I do know you can put the Ubuntu files on to a USB flash-stick to install: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
(I haven't followed these specific instructions, but they look good).

Other similar tricks: [http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive)

---

### Post by windskipper on 2008-04-07
I got the K45 barebone and build by my own the computer.
I confirm that the motherboard is able to boot on USB device.
This is how I managed to install ubuntu 7.10 using a live-USB.
Everything was recognize perfectly.

By the way, in the BIOS it is also possible to boot on USB external USB drive. external HD.

---

### Post by feed_sparky on 2008-04-23
Build your own, buy the stuff from newegg. I bought the K45 barebones kit, a 1.8ghz dual core pentium processor, 160gb HDD, and 2gb of RAM. I paid 291.37 with shipping, and I installed 8.04 using [these]("https://help.ubuntu.com/community/Installation/FromUSBStick") instructions. It's a nice little box, just wish it had pci-e instead of a regular pci.

---

