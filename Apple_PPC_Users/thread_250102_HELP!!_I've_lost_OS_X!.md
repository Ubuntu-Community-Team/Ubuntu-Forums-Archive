---
title: "HELP!! I've lost OS X!"
date: 2006-09-03
forum: Apple PPC Users
---

### Post by jave on 2006-09-03
Well, not really.  It's still on one of my hard-drives.  It's just that I can't get yaboot to recognise and boot OS X.

Recently I installed Ubuntu 6.06 onto my MDD G4/1.25DP.  After mucking around with xorg.conf to get a decent screen resolution and updating the firmware in my D-Link ADSL modem (so I could get broadband), I decided to try and get yaboot to load OS X as the default OS.  So I ran "sudo ybin".  That was where things went bad.  Let me describe my current setup.

/dev/hda - OS X lives here (IDE1 Master)
/dev/hdb - HFS+ formatted drive (IDE1 Slave)
/dev/hdc - Ubuntu 6.06 is on here (IDE2 Master)

When I ran ybin, I _think_ it installed the Apple_Bootstrap partition onto /dev/hdc.  Should it be here or on /dev/hda?  I don't think it should be on /dev/hdc, since when I start my machine, Ubuntu starts to load straight away - no boot menu at all.

Here is a copy of my current yaboot.conf:

boot=/dev/hdc2
device=hd:
#partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
macosx=/dev/hda3
default=macosx
defaultos=macosx

image=/boot/vmlinux
        label=Linux
        read-only
        append="video=ofonly"
        initrd=/boot/initrd.img
        initrd-size=8192

What do I need to do to get a boot menu so I can load OS X or Ubuntu?  Any help would be much appreciated. ](*,)

---

### Post by ssam on 2006-09-03
you could try the holding down [alt] at boot time trick. you should be given a list of partitions to boot off. that might work as a short term work around until you can fix yaboot.

---

### Post by stmiller on 2006-09-04
You don't want this line to read this way:

```
default=macosx
```

This line is to specify which kernel image, AFTER choosing to boot into Linux.

So change that back to simply:

```
default=Linux
```


The line defaultos=
is the one which you have correctly set to default to booting OS X.


And when running ybin, you have to run it with the -v option:

```
sudo ybin -v
```

and that writes everything to the correct partition. Though you have two hard drives? That could be slightly complicated, and additional paramaters might be needed with the ybin command.

If you accidently zap the OS X firmware/boot partition info, you can repair it with the OS X install disk. There's a way, somehow. Good luck!

---

### Post by jave on 2006-09-13
Thank you!  All is well now.... :)

---

