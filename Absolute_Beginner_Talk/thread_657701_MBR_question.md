---
title: "MBR question"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by codemyster on 2008-01-03
I recently did an install of a mini distro that installs to a USB stick. If i went back into Ubuntu and used GParted to format delete/format the partition, would it completely wipe the MBR?

Or is wiping the MBR unecessary to just use the USB stick as a storage medium?

I'm kinda new to booting from devices that aren't Hard Drives :lolflag:

Thanks in advanced!

---

### Post by Don1500 on 2008-01-03
Actually it makes no difference .......IF
1. You have your BIOS set up to boot from anything other than the USB stick.
and/or
2. You do not install the USB stick until after boot.

(I am assuming that you mean the MBR on the USB stick.)

---

### Post by ryanVickers on 2008-01-03
as a safety precaution, I would recommend getting super grub tool to fix it if something goes wrong...

---

### Post by codemyster on 2008-01-03
Well, Maybe i should clairify.

I DO want to wipe the MBR. If i delete the partition and format the drive, will the MBR be wiped?

---

### Post by ryanVickers on 2008-01-03
format the whole drive, I would say theres a good chance that will work
format/delete the partition, it may work...

---

### Post by iansane on 2008-01-03
Since thumbdrives are FAT format anyway it should be like a new drive. I did it in windows using disk manager once though and it works but is recognised as a drive instead of removable device or mass storage device. It still works fine in all computers and os's

---

### Post by asmoore82 on 2008-01-03
If you simply deleted/created and/or formated partitions with GParted,
the MBR should still be intact.
If, in GParted, you selected "Device -> Set disklabel ...," it would create
a completely new DOS-style partiton table and the MBR would be nuked.

---

