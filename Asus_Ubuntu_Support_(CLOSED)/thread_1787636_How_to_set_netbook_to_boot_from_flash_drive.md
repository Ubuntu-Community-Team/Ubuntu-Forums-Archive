---
title: "How to set netbook to boot from flash drive?"
date: 2011-06-21
forum: Asus Ubuntu Support (CLOSED)
---

### Post by prn on 2011-06-21
Hi Folks,

I'm trying to install ubuntu netbook remix for someone on an Asus Surf 2G.

I have used the Pendrive Universal USB Installer to format the usb drive and put UNR 10.10 on it. 

I then booted the netbook, hit F2 and went to the Boot selection in the BIOS, where I checked the Boot Device Priority and set it to:

1st Boot Device     [Removable Dev.]
2nd Boot Device     [ATAPI CD-ROM]
3rd Boot Device     [HDD:SM-SILICONMOTI]

The "Removable Dev" is presumably the usb drive, but the computer continues to boot into Xandros.  When it does boot into Xandros, it finds the usb drive and asks if I want to open it with the file manager. If I do so, I can see the files on it, so I know that the netbook is finding the usb drive and can see its files.

I assume that I am doing something stupid, but what?  Any ideas welcome.

Thanks,
Paul

---

### Post by gmargo on 2011-06-21
On my Asus EeePC, (with an AMI bios), I have to hit the Escape key during boot in order to get the option to boot from the USB.  The "Removable Device" does not refer to the USB in my case.  Presumably it refers to an attachable floppy or cdrom.

This shows up on the bios boot screen:
"Press ESC for BBS POPUP"

---

### Post by snowpine on 2011-06-21
+1; you need to hit Esc or one of the Fn keys (depending on your specific model) at boot to get the boot menu.

I'm not sure Ubuntu is a good choice for 2g Surf... you might be better with something very lightweight like Puppy.

---

### Post by prn on 2011-06-21
Thanks, gmargo and snowpine.

I will try the ESC. You may well be right, snowpine. I want to try a relatively capable distro first and then may migrate to a less full-featured distro if the netbook remix is still too sluggish. 

I'll post results here.

Thanks,
Paul

---

### Post by snowpine on 2011-06-21
I just remembered something, check the BIOS for a feature with a name like "Boot Booster" (I forget the exact name of it) and make sure it is disabled.

---

### Post by C.S.Cameron on 2011-06-21
In BIOS set your flash drive as first hard drive then make your first boot device that hard drive. Then you do not need to hit Esc when booting.

EEE PCs see flash drives as hard drives.
I use Ubuntu running from a SD card on my EEE.

---

### Post by iluminameluna on 2012-07-22
> **C.S.Cameron said:**
> In BIOS set your flash drive as first hard drive then make your first boot device that hard drive. Then you do not need to hit Esc when booting.

EEE PCs see flash drives as hard drives.
I use Ubuntu running from a SD card on my EEE.

I just found this post & I never did get my EeePC 901 to "see" my SD card, in the built-in reader, as a bootable drive. I got "Missing Operating System" every time & had to do a hard boot (holding down the power button). And I DID do the dbl setting of the Removable Drive as the first HD & additionally made it the first device to boot from.

I finally tried a Lubuntu Oneiric (11.10) stick I had to try to install ANY OS other than Ubuntu 10.10 & no dice.

I did find out that it was in part due to my having created the 10.10 SD card w/ my installation of Ubuntu 10.10 (syslinux incompatibility) but then I also found out that Sbackup won't do restores to any other OS if it's been created in Ubuntu 10.10 either. It's not written anywhere but that's my only conclusion.

I'm feeling all sorts of annoyed right now.

I've tried Wary Puppy before (I have it on a 1G SD card) but lost wi-fi connectivity & wasn't able to fix it.

My question(s):  Is there any way I can get any other *buntu OS on this netbook to boot from flash? Do I have to re-make a 10.04 LiveCd SD card-install w/ my Lubuntu install to have it work?

---

