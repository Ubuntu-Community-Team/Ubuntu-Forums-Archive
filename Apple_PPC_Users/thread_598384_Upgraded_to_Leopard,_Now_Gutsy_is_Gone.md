---
title: "Upgraded to Leopard, Now Gutsy is Gone"
date: 2007-10-31
forum: Apple PPC Users
---

### Post by fpuhan on 2007-10-31
I just took the plunge and upgraded my dual-boot G4 (1.2GHz) iBook from Tiger to Leopard.  Prior to doing so I had upgraded my Ubuntu to Gutsy, and everything was working well.

I had Yaboot configured to autoload OS X (the only tweak I made to the boot loader) as a timeout default.

However, after the Leopard upgrade, I no longer am presented with the pre-boot screen; Leopard simply starts on power up.

I have checked the disk partitions and see that my Ubuntu partition is still intact, but I'm wondering how I can restore Yaboot to give me a choice?

---

### Post by linear on 2007-10-31
Options:

1) Hold down the option key during startup to see if the Ubuntu partition is recognized by the graphical boot menu. Select from there.

2) See instructions to fix booting [here]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot"). (Look for the section titled "You lost the yaboot menu! Now what?")

---

### Post by colinhayes on 2007-10-31
hold down option as the comp boots, select the linux partition and boot into it, then run ybin.

---

### Post by stmiller on 2007-10-31
You can also  boot the alternative PowerPC CD, and boot into rescue mode. There you can pick 'restore yaboot.'

---

### Post by fpuhan on 2007-11-02
Sigh.  I did a number of things, including those suggested above (although I don't have an "alternative PowerPC CD," I only have the Edgy Boot/Install CD).

I did manage to get Yaboot re-installed, but it still refuses to boot Ubuntu.  I've tried a number of options but either get "not a valid ELF file" or "invalid or corrupt file system" or messages to that affect.

I think what I need to do is give it the entire vmlinux image name, but I don't know what it is (I upgraded to Gutsy).  In other words, at the yaboot prompt I need to enter

hd:3, /boot/vmlinux-gutsy-kernel-image-name

Does anyone have that info?

---

### Post by squidboy on 2007-11-02
have no fear you just have the osx bootloader taking over again

hold down the option key durring boot up and select the linux partition

go into Ubuntu and run ybin in console  and your done.  (might need to type sudo ybin)


All fixed.

---

