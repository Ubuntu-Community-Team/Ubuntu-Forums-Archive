---
title: "Ubuntu 10.10 64-bit not booting not installing"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by oskarloko on 2010-10-11
Hi !

I'm stuck with a problem trying to boot an Ubuntu Desktop 10.10 x64 CD into a white Macbook (2.1 gen, Core2Duo )

I've installed rEFIt, and synchronized GPT with MBR - all ok.

But when I insert the cd (works ok, the same CD on a DELL laptop ) and boot it via rEFIt, the computer hangs with this console message

```

1.

2.

Boot from Ubuntu CD-ROM:_

```
And I can't go further... ¿ anyone knows ?


Thnks

---

### Post by obast on 2010-10-11
You need the "port" version of the CD. The EFI loader on the 64-bit version doesn't work on the mac and they found it late. Its mentioned in the release notes, but its obscure. 

[http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-desktop-amd64+mac.iso)

---

### Post by oskarloko on 2010-10-15
Tried with new cd image [amd64-mac], not worked... :(

Event tried with an usb drive (using Macosx disk utils and with unetbootbin ) but also can't boot....


At least, on my girlfriend's Eee works and rocks ( but 32 bit version ) !

---

### Post by nukedeath on 2010-10-16
What benefits is there installing using the EFI Loader?

---

### Post by sunstriker on 2010-10-16
Hi,

I don't see why you want install it with an EFI bootloader. You can just use the 'emulated' MBR built in for bootcamp. If someone knows the advantages, please tell me.

This is what I did:
1. Install rEFIt
2. Boot Ubuntu from CD and run install
3. important if you also installed windows: on the screen where you configure your partitions (configure them manually) put the GRUB bootloader on the ubuntu partition itself and not on the MBR. If you don't do this, booting windows will result in ending up in GRUB again (where you will have to pick windows again), making rEFIt pointless.
4. After this I searched for instructions on how to tweak it for a Macbook (so brightness, keyboard backlight, cpu scalling et works resulting in better battery life)


I hope this helps!

---

### Post by srs5694 on 2010-10-16
> **sunstriker said:**
> I don't see why you want install it with an EFI bootloader. You can just use the 'emulated' MBR built in for bootcamp. If someone knows the advantages, please tell me.

There are significant *dis*advantages to using a hybrid MBR. They violate the standard and are an invitation to serious partitioning problems. Few tools handle hybrid MBRs safely; it's far to easy to accidentally wipe out the MBR side, accidentally damage the GPT side, accidentally create inconsistencies between the GPT and MBR sides, or otherwise mess things up. My [Web page on hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) describes their many failings. Unfortunately, these problems are all overridden by one simple issue: As a practical matter, a hybrid MBR is required to dual-boot OS X and Windows on an Intel-based Mac.

---

### Post by CoreyB. on 2010-10-17
> **srs5694 said:**
> There are significant *dis*advantages to using a hybrid MBR. They violate the standard and are an invitation to serious partitioning problems. Few tools handle hybrid MBRs safely; it's far to easy to accidentally wipe out the MBR side, accidentally damage the GPT side, accidentally create inconsistencies between the GPT and MBR sides, or otherwise mess things up. My [Web page on hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) describes their many failings. Unfortunately, these problems are all overridden by one simple issue: As a practical matter, a hybrid MBR is required to dual-boot OS X and Windows on an Intel-based Mac.

I am pretty sure Windows 7 supports UEFI, would you still need to use a hybrid MBR to dual boot OSX and Windows?

---

### Post by srs5694 on 2010-10-17
> **CoreyB. said:**
> I am pretty sure Windows 7 supports UEFI, would you still need to use a hybrid MBR to dual boot OSX and Windows?

My understanding is that Windows supports UEFI 2.x, but the Mac's version of EFI is 1.x, so Windows can't be booted on a Mac using the Mac's native EFI support; the Mac's BIOS emulation, and therefore a hybrid MBR, is still required.

---

### Post by sunstriker on 2010-10-17
> **srs5694 said:**
> There are significant *dis*advantages to using a hybrid MBR. They violate the standard and are an invitation to serious partitioning problems. Few tools handle hybrid MBRs safely; it's far to easy to accidentally wipe out the MBR side, accidentally damage the GPT side, accidentally create inconsistencies between the GPT and MBR sides, or otherwise mess things up. My [Web page on hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) describes their many failings. Unfortunately, these problems are all overridden by one simple issue: As a practical matter, a hybrid MBR is required to dual-boot OS X and Windows on an Intel-based Mac.

Thanks for the info. But how big are the changes of really screwing up the GPT/MBR table? I always do my partitioning in Mac OS X and rEFIt has a tool to sync the MBR with the GPT. So I've never ran into problems before...

---

