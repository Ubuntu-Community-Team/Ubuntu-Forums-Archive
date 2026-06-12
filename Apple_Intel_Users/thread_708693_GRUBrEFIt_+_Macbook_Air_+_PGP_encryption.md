---
title: "GRUB/rEFIt + Macbook Air + PGP encryption"
date: 2008-02-26
forum: Apple Intel Users
---

### Post by Justa82 on 2008-02-26
I have a bizarre scenario at work: boss wants to use a Macbook Air running Windows XP.  He ALSO wants to encrypt the XP partition with PGP whole disk encryption.  

Now, I've seen a [few posts]("http://ubuntuforums.org/showthread.php?t=594298") around here re: multi os boot, but none that address my specific issue.  Because of the way PGP encrypts the disk, apparently it wipes out the bootloader after you encrypt the volume.  I've fooled around w/bootcamp (successfully), as this was my attempt at getting this stuff working, but after installing PGP and encrypting the XP partition, I restart and get a "bootguard loading stage2".  I'm convinced (so is the PGP tech dude) that if I install things in the right order, I should be able to use GRUB as my bootloader so that I don't get this error.  Any suggestions are certainly appreciated...if you need clarification, let me know.

---

### Post by cyberdork33 on 2008-02-26
you want to dual boot, or just use windows?

---

### Post by Justa82 on 2008-02-27
Either.  I don't mind throwing Ubuntu on there, or Leopard...but he wants to run XP as the default OS (i.e. no splash/boot screen).  I've been able to get bootcamp up and running w/Leopard/XP just fine...it's PGP that's ruining my day.  I don't know if I need a dual-boot environment to get this to work...but the ultimate goal is getting XP + PGP whole disk encryption running on a macbook air.

---

### Post by cyberdork33 on 2008-02-27
> **Justa82 said:**
> Either.  I don't mind throwing Ubuntu on there, or Leopard...but he wants to run XP as the default OS (i.e. no splash/boot screen).  I've been able to get bootcamp up and running w/Leopard/XP just fine...it's PGP that's ruining my day.  I don't know if I need a dual-boot environment to get this to work...but the ultimate goal is getting XP + PGP whole disk encryption running on a macbook air.You are going about it the right way in my opinion (You will want OS X for updates, especially on hardware that new). You can install Grub from windows with Wingrub if that will help you, but I can give much advice on the whole-disk encryption:
[https://sourceforge.net/projects/grub4dos](https://sourceforge.net/projects/grub4dos)

If it is true that the bootloader is getting wiped, then IDK how much grub will help, but I don't really understand the process that is used to unlock the partition and boot. Stage2 is usually stored on the filesystem of the root partition you are booting and contains the actual grub files, stage1 is stored in the MBR (usually) and just loads stage2 (or stage1.5 if it is needed for your setup). From what the error looks like, the "replacement" bootloader that is used is looking for the stage2 file and cannot find it (doesn't exist?) or it can't read it for some reason.

---

