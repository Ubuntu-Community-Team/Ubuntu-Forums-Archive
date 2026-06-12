---
title: "Problem booting with a Persistent Live-USB"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by Kiljaeden on 2008-06-22
Hi,
I tryed to create a persistent live-USB on a 1GB USB key, following the how-to provided [here]("http://doc.ubuntu-fr.org/live_usb_persistent"). (yes, in fact, I'm French, that's why it's from Ubuntu-fr.org).
All was great, I made commands *install-mbr* and *syslinux -f* to make the USB key a boot device. And then, I verify with GParted, and the Fat32 partition of the USB-Device is, actually, a boot device.
But, when I boot my iMac (5th gen, with Intel Core2Duo proc), with the 'ALT' key down, I only see the HDD with Mac OS, and without holding this key, Mac OS X boot, as usual.
So there's a problem... ^^ My key is not recognized yet by the iMac's EFI, in fact.
I wanna find a good way to boot on my live-USB.
If someone can help me, it'll be great !
And, one more thing complicated : I don't want to touch my internal HDD at all nor my Mac OS X system.

Thanks,

P.S.: French users, if there are, can find a [similar topic]("http://forum.ubuntu-fr.org/viewtopic.php?id=230835") on Ubuntu-fr forums. (and sorry again for my bad English)

---

### Post by Kiljaeden on 2008-06-23
Humph... Nobody knows ? :(
In fact, after some searches, I found out that Apple's EFI can't boot on MBR. But I'm not sure at all. Morever, to boot on MBR with this EFI, rEFIt is needed, but (I think), to install rEFIt, we have to modify the Mac OS X system, and I don't want to.
Any solutions ?

---

### Post by Kiljaeden on 2008-06-23
Hum, sorry to post again, but I found out [a method]("http://refit.sourceforge.net/doc/c1s1_install.html") to install rEFIt on an external drive, such as USB pendrives, and I tryed :
Holding down 'ALT' during the boot, two disks appear : my internal HDD (normal), and my Live-USB. If I select this one, I have the rEFIt menu. At this point, all's good. But, after that, if I select Ubuntu system to boot, I have an error message, which is, to me, from Apple's EFI.
Here's this error screen : (it's the same screen on the two photos, but I send two because of quality...)
[[IMG]http://walhalla.teria.org/bootefi_m.jpg[/IMG]]("http://walhalla.teria.org/bootefi.jpg")
[[IMG]http://walhalla.teria.org/bootefi1_m.jpg[/IMG]]("http://walhalla.teria.org/bootefi1.jpg")
I don't know at all where it is from.
If anybody can help me...

Note : I'm running Mac OS X v.10.4.11

---

### Post by cyberdork33 on 2008-06-23
macs won't boot a "legacy OS" from USB (yet anyway). See the topic linked in the FAQ.

---

