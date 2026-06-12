---
title: "Help booting from Ubuntu 7.04 PPC CD with PowerBook G3's"
date: 2007-05-28
forum: Apple PPC Users
---

### Post by TC10284 on 2007-05-28
Hey all,

I am new to these forums. First off, I'd like to say that yes, I am a hardcore PC guru, but I got some PowerBook G3's and some older laptops at a school auction and I'd LOVE to learn more about Mac's for personal reason and possibly for work reasons. 

Anyway, The PB G3's are in good condition. I have two G3's and only one floppy/battery/CD-ROM drive/power adapter for both. Both have around 2GB HD's.
Both laptop HDs have been wiped clean with a data destruction program. Therefore, MacOS is not installed and I don't have a MacOS CD for the systems. I have been researching how to install a distro of Linux on to the G3's. All the guides I see say to press and hold C (or ctrl-option-shift-del) while the system powers on after hearing the Apple sound. I have the Ubuntu CD in the CD drive and I hear the drive spin up but I always get the question mark in a floppy. I have tried this on both systems (even some old 117/166MHz systems), but the only thing I can get is a flashing question mark in a floppy disk. I have tried Ubuntu 7.04 and Yellow Dog Linux 5.01, both for PowerPC arch. I am getting frustrated

Can anyone give me any assistance on how to get the systems to boot from CD? I'd really like to use Ubuntu on these.

---

### Post by Auria on 2007-05-28
i dont reckon ctrl-option-shift-del is an option to boot a CD...

did you try alt key?

anyway it seems like you either choose the wrong CD (you need the ppc one, check the sticky for download lcoation) or you did not burn properly (burn slowly, burn the contents of the ISO and not the ISO file on the CD, some older macs have prolbems with CDs and prefer CD-RWs but i have no idea if this applies to your computer)

---

### Post by stmiller on 2007-05-28
Read the PPCFAQs at the link below. If these are oldworld macs (I think they are?), you'll have to follow the old world instructions, and that requires a Mac OS 9 install CD to set up Linux. 

Holding down 'C' is the correct method to boot from a CD.

---

### Post by TC10284 on 2007-05-28
> **Auria said:**
> i dont reckon ctrl-option-shift-del is an option to boot a CD...

did you try alt key?

anyway it seems like you either choose the wrong CD (you need the ppc one, check the sticky for download lcoation) or you did not burn properly (burn slowly, burn the contents of the ISO and not the ISO file on the CD, some older macs have prolbems with CDs and prefer CD-RWs but i have no idea if this applies to your computer)


I have
 ubuntu-7.04-desktop-powerpc.iso

I burned the ISO using Nero using the burn from image mode. I'll try the slower burn and CD-RWs but I honestly think it's not that. 

Is there a key combination with alt?

---

### Post by pxwpxw on 2007-05-29
I think the base problem is that with no macos installed and wiiped clean, there is no bootloader to load the cd, and tthe mac open frimware is set boot-device to load from harddisk.

You can open Open Firmware by holding down Command Alt O F during strartup,
ithen in open firmware do 

printenv

that will list boot-device. Then you can change that using

setenv boot-device cd:,\\:tbxi

(from memory)

That probably only applies for a NewWorld mac.

Possibly easier to install a minimal macos9 as stmiller says above.

---

### Post by stmiller on 2007-05-29
> **pxwpxw said:**
> I think the base problem is that with no macos installed and wiiped clean, there is no bootloader to load the cd, and tthe mac open frimware is set boot-device to load from harddisk.

Well, having a bare drive doesn't make any difference. Holding 'C' should work. But I did a quick glance, and yes looks like this is an old world mac. So it cannot boot this live CD.

You will have to follow the oldworld mac how-tos linked from the FAQs below:

---

### Post by pxwpxw on 2007-05-29
PowerBook G3 Computers: How to Identify Different Models

[http://docs.info.apple.com/article.html?artnum=24604](http://docs.info.apple.com/article.html?artnum=24604)

More clues here:
(powerbooks cover both eras)

Old World/New World (explanation)

[https://help.ubuntu.com/community/OldWorld](https://help.ubuntu.com/community/OldWorld)

A macos9 install CD would help.

edit:

 just checked on my old world powermac 7300, and it gives (in open firmware)
```

0> printenv boot-device
/AAPL,ROM

```

which I think is the definition of old world.

---

