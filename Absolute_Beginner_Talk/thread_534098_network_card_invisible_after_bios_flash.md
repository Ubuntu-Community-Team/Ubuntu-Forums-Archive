---
title: "network card invisible after bios flash"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by dsbw on 2007-08-24
I recently flashed my bios (AMIBIOS on an MSI motherboard, AMD 2400) and rebooted Ubuntu Server to discover my onboard NIC undetectable. I tried to do a repair from the CD but it couldn't detect the NIC either.

Not sure how to proceed.

---

### Post by DBStevens on 2007-08-24
Is the bios setting for the onboard nic set to off or disabled by any chance?

---

### Post by Paulmd on 2007-08-25
> **dsbw said:**
> I recently flashed my bios (AMIBIOS on an MSI motherboard, AMD 2400) and rebooted Ubuntu Server to discover my onboard NIC undetectable. I tried to do a repair from the CD but it couldn't detect the NIC either.

Not sure how to proceed.

You used the correct BIOS for your motherboard???? 

I did this once on a Biostar Motherboard. There were 2 very similar series of motherboards, but the one with LR in the name had the integrated Ethernet (LR stood for Lan Ready). But when using the version that didn't specify LR, well.... The result was that the motherboard was no longer Lan Ready. :) The solution was to put the old BIOS back. 

But before you do, go through the bios settings and make sure that the onboard lan is enabled.

---

### Post by dsbw on 2007-08-25
Thanks, guys.

Yeah, I'm sure it was the right BIOS. It's beautiful. I've been having trouble with this thing locking up solid (Windows and Linux and, hell, MemTest86+) and it hasn't locked up since I flashed it. Though, USB doesn't work when booting, either. I think these are all clues to what was going on before. Or maybe I've been taken one too many hits with the snake.

And yeah, the onboard NIC is enabled. I thought of that right after I posted. 

From some searching it seems that, maybe it's an IRQ problem. I note that lspci shows the chip as being there but network manager sez no network interface is found.

Any other thoughts?

---

### Post by Paulmd on 2007-08-25
> **dsbw said:**
> Thanks, guys.

Yeah, I'm sure it was the right BIOS. It's beautiful. I've been having trouble with this thing locking up solid (Windows and Linux and, hell, MemTest86+) and it hasn't locked up since I flashed it. Though, USB doesn't work when booting, either. I think these are all clues to what was going on before. Or maybe I've been taken one too many hits with the snake.

And yeah, the onboard NIC is enabled. I thought of that right after I posted. 

From some searching it seems that, maybe it's an IRQ problem. I note that lspci shows the chip as being there but network manager sez no network interface is found.

Any other thoughts?

I take it that you have a dual Boot Setup, and the NIC works in Windows? I'm sorry if I'm misreading between the lines. :) 

If you still have that install CD handy, try using it as a live CD and browsing the internet.

In windows, I would uninstall the device with the device manager, and then force it to re-detect. In Linux, I'm not quite sure how to do that, except the long way. Here goes:

Go into the BIOS, disable the Nic, save changes and exit. Boot back in to Ubuntu. Once there, run lspci, and make sure that the nic isn't listed. Reboot.

Go back in to the BIOS, re-enable the nic, save and exit, reboot back in to linux. Wait a vew minutes, then try browing the internet. If that doesn't work. Reboot once more, and try browsing the internet again. If it still doesn't work... you can stop rebooting. :) 

There is probably a more elegant method of doing this.  (Ubuntu really needs a better device manager. Hope it's one of those things that gets worked into Gutsy)

---

### Post by dsbw on 2007-08-25
> **Paulmd said:**
> I take it that you have a dual Boot Setup, and the NIC works in Windows? I'm sorry if I'm misreading between the lines. :) 

I haven't tried Windows since flashing the BIOS. I had a problem with it messing up my video and I really didn't want it. I'm trying it now....

> **Paulmd said:**
> If you still have that install CD handy, try using it as a live CD and browsing the internet.

Does not work. Well, I put in Kubuntu 7.04 and it didn't work. 

> **Paulmd said:**
> Go back in to the BIOS, re-enable the nic, save and exit, reboot back in to linux. Wait a vew minutes, then try browing the internet. If that doesn't work. Reboot once more, and try browsing the internet again. If it still doesn't work... you can stop rebooting. :) 

Yeah, no dice. lspci lilsts the device but the Network Manager says no interfaces found.

It doesn't work under Windows either.:shock: Windows sees it and says, yeah, it's there but it doesn't connect. Garf.

---

### Post by Paulmd on 2007-08-25
> **dsbw said:**
> I haven't tried Windows since flashing the BIOS. I had a problem with it messing up my video and I really didn't want it. I'm trying it now....



Does not work. Well, I put in Kubuntu 7.04 and it didn't work. 



Yeah, no dice. lspci lilsts the device but the Network Manager says no interfaces found.

It doesn't work under Windows either.:shock: Windows sees it and says, yeah, it's there but it doesn't connect. Garf.


Well... I think the bios flash did somehow mess with your NIC, but i also see that you have a good reason for not reverting to the old bios (computer stopped freezing is a  good enough reason ). I'm going to propose a workaround: disable the onboard nic, get a pci nic. If you can scrounge up an old 3com 3c905b (or c), another good one is the Intel pro/100 (in its various permutations).   That's the cheap way. 

As far as choosing a new nic is concerned, for a home user, there's really not much difference in performance, and even an old 10 base card will be fine for connecting to high-speed internet. If you buy a new in the box nic, just make sure it has linux support (it should say right on the box).  Intel and 3com are good about this, but so are many other brands.

---

### Post by Paulmd on 2007-08-25
> **Paulmd said:**
> Well... I think the bios flash did somehow mess with your NIC, but i also see that you have a good reason for not reverting to the old bios (computer stopped freezing is a  good enough reason ). I'm going to propose a workaround: disable the onboard nic, get a pci nic. If you can scrounge up an old 3com 3c905b (or c), another good one is the Intel pro/100 (in its various permutations).   That's the cheap way. 

As far as choosing a new nic is concerned, for a home user, there's really not much difference in performance, and even an old 10 base card will be fine for connecting to high-speed internet. If you buy a new in the box nic, just make sure it has linux support (it should say right on the box).  Intel and 3com are good about this, but so are many other brands.

One more thing: An unhappy thought is that your motherboard could be bad. It would explain the freezing, the video issues, and a host of symptoms you had pre-flash, and post flash. Open up the computer and look at the capacitors (they look like little soda cans) if any are bulging or leaking, even a tiny bit, they're bad, and you need a new motherboard. -- it is possible to replace the capacitors, but few shops will do the work for less than the replacement cost of the motherboard, as it involves a considerable amount of time and skill.

---

### Post by dsbw on 2007-09-06
> **Paulmd said:**
> Well... I think the bios flash did somehow mess with your NIC, but i also see that you have a good reason for not reverting to the old bios (computer stopped freezing is a  good enough reason ). I'm going to propose a workaround: disable the onboard nic, get a pci nic. If you can scrounge up an old 3com 3c905b (or c), another good one is the Intel pro/100 (in its various permutations).   That's the cheap way. 

As far as choosing a new nic is concerned, for a home user, there's really not much difference in performance, and even an old 10 base card will be fine for connecting to high-speed internet. If you buy a new in the box nic, just make sure it has linux support (it should say right on the box).  Intel and 3com are good about this, but so are many other brands.

Yeah, I was going to go for an old NIC. I know I have some lying around. I've never had a problem with any NIC in Linux. (Well, except this one, but that's not Linux-specific.)

---

### Post by dsbw on 2007-09-06
> **Paulmd said:**
> One more thing: An unhappy thought is that your motherboard could be bad. It would explain the freezing, the video issues, and a host of symptoms you had pre-flash, and post flash. Open up the computer and look at the capacitors (they look like little soda cans) if any are bulging or leaking, even a tiny bit, they're bad, and you need a new motherboard. -- it is possible to replace the capacitors, but few shops will do the work for less than the replacement cost of the motherboard, as it involves a considerable amount of time and skill.

I bought this machine in 2002 and have had problems with it since I got it. Over the years, in trying to fix it, the guy I bought it from has replaced *everything* over the years, including the motherboard. (And free of charge, which is fair on the one hand, but over five years is probably above-and-beyond.) What I think, though, is that the BIOS was probably the same between the two MBs, so that the USB issue conflict remained.

This is something of a knack I have. I manage to buy *the *peripheral that conflicts with the motherboard, but you have to wade into the deepest levels of a Taiwanese website to find that out.

But it's been rock solid since I did the flash, so adding a NIC is a cheap and happy solution.

Thanks.

---

