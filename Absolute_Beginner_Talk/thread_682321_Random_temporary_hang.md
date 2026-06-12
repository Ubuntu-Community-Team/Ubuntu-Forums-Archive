---
title: "Random temporary hang"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by wagenseil on 2008-01-29
Hello -- total newbie here.

Ubuntu randomly hangs for 10-15 seconds, with only the cursor responding,  Music or movie will stop playing, then everything starts again after a bit.  Happens every 10 or 20 minutes, more so when typing or using Firefox.

I've seen similar problems blamed on various graphics cards in these forums, but mine's about as basic as it gets -- Intel GMA 900 integrated.

I'm using Gutsy now, but this happened in Edgy and Feisty too,

System specs: Acer TravelMate 5602WSMi laptop | Pentium M 1.7 GHz | 17-inch widescreen LCD | 1 GB DDR2

Thanks.

---

### Post by asmoore82 on 2008-01-29
check the output of ```
dmesg
``` immediately after a "hang-up."

---

### Post by wagenseil on 2008-01-29
i ran it and got multiple instances of this:

[ 5909.448000] ata1: port is slow to respond, please be patient (Status 0xd0)
[ 5914.432000] ata1: device not ready (errno=-16), forcing hardreset
[ 5914.432000] ata1: soft resetting port
[ 5914.792000] ata1.00: configured for UDMA/100
[ 5914.988000] ata1.01: configured for UDMA/25
[ 5914.988000] ata1: EH complete

I'm guessing that has something to do with communicating with the hard drive.

---

### Post by wagenseil on 2008-01-29
aha, happened again.  immediately afterward, here's what dmesg came up with:

[ 6335.160000] ata1.01: qc timeout (cmd 0xa0)
[ 6335.160000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 6335.160000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[ 6335.160000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[ 6340.200000] ata1: port is slow to respond, please be patient (Status 0xd1)
[ 6345.184000] ata1: device not ready (errno=-16), forcing hardreset
[ 6345.184000] ata1: soft resetting port
[ 6345.544000] ata1.00: configured for UDMA/100
[ 6345.732000] ata1.01: configured for UDMA/25
[ 6345.732000] ata1: EH complete

---

### Post by asmoore82 on 2008-01-29
that would seem to indicate hardware failure of your hard drive.

---

