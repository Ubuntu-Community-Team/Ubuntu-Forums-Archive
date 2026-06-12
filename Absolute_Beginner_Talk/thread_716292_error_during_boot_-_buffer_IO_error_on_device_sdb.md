---
title: "error during boot - buffer I/O error on device sdb"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-05
AGHHH!! okay. im getting frustrated. Ubuntu will no longer boot. not even from the live disk.

When I boot in recovery mode I get a bunch of these error messages

"[      xx.xxxxxx] Buffer I/O error on device sdb, logical block 1xxxxxx"
and I saw this one pop up once as well
"ldm_validate_partition_table(): Desk read failed."

Does this mean that my hard drive has gone bad? That wouldn't explain why the live disk wouldn't boot though. I was going to try to run fsck or something like that to test the hard drive but I can't get into ubuntu.

in recovery mode after is spews out a couple of those messages it just stops and leaves me with a blinking cursor and if i type something then i get some kind of shell prompt saying something like root@computername~# (I don't remember exactly)

can I run something from that?

To cause this sll I did was change my xorg.conf file and disabled xinerama by changing "true" to "false"

I ran dskchk from windows XP on the hard drive but I'm not sure if that would run it on the linux partition that is on that drive. It said it found an error but that it fixed it.

---

### Post by lincolnastic on 2008-03-05
I believe sdb devices are USB. I would unplug any USB storage devices you have pluged in and then try and boot again...Unplug any devices for that matter.

IF it does come down to a suspected hard drive, you can unplug the power and data cables from it and try to boot from the Ubuntu CD again.

---

### Post by elchico04 on 2008-03-05
thanks that worked. Did I confused sdb with sda?
Well I'm glad that I learned something new about this strange complicated world of linux.

---

