---
title: "ALL Linux distributions run on the MAC ?"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by lse123 on 2009-01-02
May I run one of kubuntu or ubuntu from usb flash drive(bootable) or cd live(bootable) , from a MAC MINI(I plan buy an intel 2 one_2.0GHz_latest) ?
ALL Linux distributions run on the MAC ?

---

### Post by Alterax on 2009-01-02
Well, it really depends on your Mac mini.  Is it using the Core Duo processor, or does it use the G4 or G5 processor?

The reason I am asking this is to find out the architecture of your system.  That will let you know if you need the standard install CD (x86 for the Core Duo), or if you need the PowerPC version (for the G4 or G5).

As far as whether or not all versions will run on it, that depends again on the architecture.  The x86 is the most common, and most distributions have builds capable of running on that. If you have a PowerPC, it's a bit tougher, as there are fewer versions that run on it.

Finally, as far as running off a USB drive, I don't see why not.  Boot from the appropriate Ubuntu CD, with the USB drive plugged in.  Follow the instructions to put it all on your USB drive and make sure it puts the bootloader on that device too.  Then when you're ready to boot up, plug in the drive and power up the mac while holding down OPTION.  It should detect the USB drive as a potential boot device.

Have fun!

---

### Post by Skripka on 2009-01-02
> **lse123 said:**
> May I run one of kubuntu or ubuntu from usb flash drive(bootable) or cd live(bootable) , from a MAC MINI(I plan buy an intel 2 one_2.0GHz_latest) ?
ALL Linux distributions run on the MAC ?


Unless you have a bizzarro processor architecture unknown to man-you can run any kind of linux on virtually any hardware.  Mac hardware is just regular old PC hardware in a pretty box.

---

### Post by lse123 on 2009-01-02
intel 2 CORE DUO _ 2.0GHz_(latest) MAC MINI needs only and non else appropriate the 64bit ver of Linux or ... ? 32bit can NOT run, correct ?

---

### Post by lse123 on 2009-01-02
ubuntu.com ships free ONLY 32bit cdroms ?

---

### Post by DGortze380 on 2009-01-02
> **lse123 said:**
> intel 2 CORE DUO _ 2.0GHz_(latest) MAC MINI needs only and non else appropriate the 64bit ver of Linux or ... ? 32bit can NOT run, correct ?

I'm not quite sure what you're asking.

You can run either x86 (32-bit x86) or x86_64 (64 bit x86) versions of Ubuntu/Kubuntu/Distro of Your Choice on an Intel CoreDuo or Core2Duo. 

If it's a G4, you need the PowerPC (PPC) build, I suggest Ubuntu 7.10 and yaboot.

Don't know if there ever was a G5 in the Mini, but thats a 64 bit PPC, and yet another separate build.

---

### Post by DGortze380 on 2009-01-02
> **lse123 said:**
> ubuntu.com ships free ONLY 32bit cdroms ?

Just download and burn the iso if you have the bandwidth available. It's easier and faster.

---

### Post by cyberdork33 on 2009-01-05
> **Alterax said:**
> Finally, as far as running off a USB drive, I don't see why not.  Boot from the appropriate Ubuntu CD, with the USB drive plugged in.  Follow the instructions to put it all on your USB drive and make sure it puts the bootloader on that device too.  Then when you're ready to boot up, plug in the drive and power up the mac while holding down OPTION.  It should detect the USB drive as a potential boot device.
Booting what Apple calls "legacy" operating systems from an external device does not work unless you do some grub-efi magic.

---

### Post by pxwpxw on 2009-01-05
And an Intel Mini, using i386 32bit kernel should boot grub.efi from external (model 2,1 - not sure if that is the current model).

---

