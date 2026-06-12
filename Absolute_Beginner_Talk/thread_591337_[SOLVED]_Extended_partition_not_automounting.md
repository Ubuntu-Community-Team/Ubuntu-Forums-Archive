---
title: "[SOLVED] Extended partition not automounting"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by laidback on 2007-10-25
I'm having an inconsistency with the automounting of my USB hdd. The latest partition that I've created within an Extended Partition will not automount. I created it within Gparted in the same way as I've always done. See screen image attached.

/dev/sda8 won't automount, neither will it take a new label using e2label.
I can mount it in the normal way via a terminal, but I think there's something here that I don't understand as this is new behaviour, all the other partitions automount.

Many thanks

Laidback

---

### Post by laidback on 2007-10-26
Anyone?

---

### Post by MegaJim on 2007-10-26
so, when you do mount-a you don't get any errors?

have you tried looking through dmesg after boot?

---

### Post by laidback on 2007-10-26
Sorry for slow response...power failure.
Can't see anything in dmesg that indicates a problem. The problem is on a USB drive that I don't normally switch on, but when I do I'm used to seeing it automount with icons for each partition, including those within the extended partition, appearing on the desktop. It just stops doing this for /dev/sda8. I've spent ages trying to think what I've done that's different but have come up with zero. I've even deleted sda8 and recreated it, still no go.
Many thanks for your response.

---

### Post by laidback on 2007-10-27
Should anyone be interested I've now got a copy of 7.10 and with this version my USB drive autoboots all the current partitions including the previously missing /dev/sda8 which also has the label I attermpted to give it using e2label, which also appeared not to be working in 7.04. Ah well, at least I know I was trying to do the right thing even though it didn't work. I still don't understand what was happening though.

---

