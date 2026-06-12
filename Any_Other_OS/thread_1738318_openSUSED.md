---
title: "openSUSED"
date: 2011-04-24
forum: Any Other OS
---

### Post by doppel.ganger on 2011-04-24
I just downloaded openSUSE 11.4 DVD version. I want to put it on my 16 gig thumb drive. When I open the Startup Disk Creator in Admin, hit Other, select the suse ISO and hit ok, it does not show up in the space. I'm openSUSED!:confused:](*,) I would also like to know whether this DVD version is GNOME or KDE.

---

### Post by coffeecat on 2011-04-24
Startup Disk Creator only works with Ubuntu ISOs. Try using unetbootin which you can install from the repositories.

---

### Post by howefield on 2011-04-24
Thread moved to "*Other OS/Distro Talk*"

---

### Post by andymorton on 2011-04-25
If you're comfortable with the command line then you can do the following - 

sudo dd if=/*path to the .iso* of=/*path to your usb stick*

for example - 

sudo dd if=/home/doppel.ganger/Downloads/openSUSE-11.4-dvd.iso of=/dev/sdb

You'll need to check the path to you USB stick. Mine always says /dev/sdb but yours may be different.

andy

---

### Post by el_koraco on 2011-04-25
Check openSUSE's page. AFAIK, you have to manually put the iso on the stick, Unetbootin will not help.

---

### Post by screaminj3sus on 2011-04-25
Its been a while since I used the suse dvd version, but afaik the dvd has both gnome and kde and lets you choose during install.

---

### Post by wolfen69 on 2011-04-25
> **andymorton said:**
> If you're comfortable with the command line then you can do the following - 

sudo dd if=/*path to the .iso* of=/*path to your usb stick*



dd=data destroyer. I wiped out 35,000 mp3's with that command. :(

Yeah, I know, my fault. But still.

---

### Post by C.S.Cameron on 2011-04-25
MultiBootUSB has just been updated to boot openSUSE isos from USB.
It's magic.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

