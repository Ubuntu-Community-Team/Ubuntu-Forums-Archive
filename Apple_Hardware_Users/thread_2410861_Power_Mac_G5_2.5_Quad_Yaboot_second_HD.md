---
title: "Power Mac G5 2.5 Quad Yaboot second HD"
date: 2019-01-21
forum: Apple Hardware Users
---

### Post by ozark4 on 2019-01-21
I am fairly new to Ubuntu and having some issues configuring yaboot to recognize the second hard drive which has another Ubuntu installation I would like to have the option to boot from. No OS X installed at all. Any help would be appreciated.

ybin: Finding OpenFirmware device path to `/dev/sda2'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sda2...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sda2...
ybin: Installing /etc/yaboot.conf onto /dev/sda2...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sda2 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...

The second hd does not mount automatically on boot.

---

### Post by gsahli on 2019-01-21
You didn't say if you've run the command sudo ybin -v ?

---

### Post by ozark4 on 2019-01-22
I have and it installed yaboot on both /dev/sda2 and /dev/sdb2 but when I boot I only get the options Linux and old

---

### Post by gsahli on 2019-01-22
OK, I see you added the ybin output after I asked the question Thanks. Looks like you need to boot into Open Firmware to get the paths to your two drives so you can add that into yaboot.conf.
I haven't done that recently.
Read:
[http://mac.linux.be/content/guide-open-firmware-apple-bios-0](http://mac.linux.be/content/guide-open-firmware-apple-bios-0)
[http://osxbook.com/book/bonus/ancient/whatismacosx/arch_boot.html](http://osxbook.com/book/bonus/ancient/whatismacosx/arch_boot.html)
[http://www.firmworks.com/QuickRef.html](http://www.firmworks.com/QuickRef.html)
I "think" I remember that the command devalias will give you your drives boot names to put into yaboot.

---

