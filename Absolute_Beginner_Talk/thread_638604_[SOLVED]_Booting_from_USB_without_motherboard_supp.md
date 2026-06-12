---
title: "[SOLVED] Booting from USB without motherboard support"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by shadow-of-sin on 2007-12-12
Ok, so I'm stuck with an old Dell Optiplex GX240 for a month (the worst part is that it has XP on it...and with only 128MB of RAM it runs really slow). I want to install DSL onto a thumbdrive and boot into it, so I followed the instructions here:
[http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl](http://www.pendrivelinux.com/2007/01/02/all-in-one-usb-dsl) (except I used the latest version: 4.1 instead of the one linked to in that article). Now here's the problem: the motherboard does not support USB booting. So how would I go about booting from the USB drive? I have tried using Super Grub Disk but it wont recognise the partition on the pendrive (also I realize that it would be easier to install onto a CD but this computer has no CD burner :( ).

Thanks in advance,

---

### Post by rockinlinux on 2007-12-12
im pretty sure that if you cant enable USB booting in the bios it is impossible to boot from USB devices. :(

---

### Post by shadow-of-sin on 2007-12-12
> **rockinlinux said:**
> im pretty sure that if you cant enable USB booting in the bios it is impossible to boot from USB devices. :(

Really? I remember reading somewhere that you can install GRUB onto the MBR of the internal hard disk and then change some options to boot linux from a USB drive...however I can't find that link for reference

---

### Post by shadow-of-sin on 2007-12-12
Ah I got it...I overlooked the fact that DSL have a boot disk on their website for computers that don't support USB booting. Tested it out and it works fine :D Now to get the net working in DSL...

---

### Post by Zylar on 2008-01-11
Sorry to hijack, but I'm wondering if there's something similar to this for Ubuntu? 

I have a [live-persistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") 7.10 install on a 40g external usb hd that will only boot from 2 of my 4 testbeds, due to lack of usb-boot support in the bioses.  

I've found the DSL floppy you describe and a [Wolvix]("http://wolvix.org/node/344") floppy that'll do the same, but I imagine they're both customized for their respective distros (both of which are small).  

The topic fits perfectly, too bad it's solved and not related to Ubuntu, so hopefully someone will stop by and be able to help me out.

Thanks,

---

