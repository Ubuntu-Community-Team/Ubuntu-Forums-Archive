---
title: "Installing ubuntu to external(to make drive internal)"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by johnlee on 2007-07-06
hi heres the details
laptop which doesnt boot from usb or have cd in it
ive pulled out the hard drive, mounted it in a external enclosure, not i want to install ubuntu (from another computer) on it so i can remount it in the laptop
the posts ive read all want to boot from the usb, i want to load the os though the usb then mount internally

howto?
thanks

---

### Post by logos34 on 2007-07-06
is this a blank drive?

---

### Post by p_quarles on 2007-07-06
I really don't think you want to do that -- if you install it to an external drive on a separate computer, it's going to optimize the installation for that computer. Even if you did manage to get it to work (I have no idea how), you would end up with a messy installation that would take forever to get to work. 

Imagine: you install it on a desktop, and then put that drive in a laptop, and you're going to have no touchpad support, desktop energy management setting, the wrong graphics driver, etc., etc. 

See if the BIOS on the laptop supports booting from a USB drive. If it does, go get a USB flash key, write the installation .ISO to that and go from there.

---

### Post by johnlee on 2007-07-06
it doesnt support usb boot :S toshiba protege 3500, and only vendor cd drives work for boot :(

---

### Post by twiceasworn on 2007-07-06
> **p_quarles said:**
> I really don't think you want to do that -- if you install it to an external drive on a separate computer, it's going to optimize the installation for that computer. Even if you did manage to get it to work (I have no idea how), you would end up with a messy installation that would take forever to get to work. 

Imagine: you install it on a desktop, and then put that drive in a laptop, and you're going to have no touchpad support, desktop energy management setting, the wrong graphics driver, etc., etc. 

See if the BIOS on the laptop supports booting from a USB drive. If it does, go get a USB flash key, write the installation .ISO to that and go from there.

Agreed, the only way you could feasibly make this work is if the two machines had an identical hardware setup.

---

### Post by johnlee on 2007-07-06
ei! how about installing on the disk a server install or something and then doing the instal while the drive is in
or could i put the iso on the drive, a unpacker and some5hing to issue commands? (could i make the hard drive look like a cd drive for awhile?

---

### Post by p_quarles on 2007-07-06
> **johnlee said:**
> it doesnt support usb boot :S toshiba protege 3500, and only vendor cd drives work for boot :(
In other words, you couldn't boot from an external CD drive? That sucks.

The one other option I can think of is booting from a network connection. I've never done it, but I know it CAN be done, if the BIOS on the laptop will support it. It would require setting up an FTP server on your network, and then loading the installation image into that.

---

### Post by p_quarles on 2007-07-06
Ha, simultaneously posted the same idea. But, yeah, you can boot from a network location, I just don't know how, exactly.

Putting the .ISO on the hard drive *might* work, but it would probably be really hard to get it to boot from there. Maybe someone else knows.

---

### Post by johnlee on 2007-07-06
it does support lan boot,
however is there a way i can partition the now external drive to look like a cd drive?

---

### Post by p_quarles on 2007-07-06
Well, I searched for a tutorial on LAN install, and found something that explains how to do that as *well as* an install from a hard disk .ISO partition. Try this?

[http://ubuntuforums.org/showthread.php?t=880](http://ubuntuforums.org/showthread.php?t=880)

Second message down. Let us know if it works.

---

### Post by johnlee on 2007-07-17
i caved and ended up buying a pcmia card cd rom drive which will hopefully work
fingers crossed
thanks guyes

---

