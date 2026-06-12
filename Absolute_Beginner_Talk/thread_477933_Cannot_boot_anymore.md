---
title: "Cannot boot anymore"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by TheDewAddict on 2007-06-18
This morning, I tried to load Firefox on my Ubuntu box.  I got the "starting Firefox" message, but then nothing.  I tried to load the Terminal, and got the same thing.  I decided to reboot, but first I wanted to save a spreadsheet.  I tried saving it, but I got a message saying the filesystem was "read-only"

I went ahead and rebooted, but now I get the message: "can't access tty; job control turned off"  I've read all the threads about that, but that's not why I'm posting this.  I've booted into the Live CD, since all I really want to do is pull some data off my disk, and then clear it.  However, I'm unable to mount the disk.  When I try:

sudo mount -t ext3 /dev/hda1 /mnt

I get:

```

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So I tried: dmesg | tail, and this is what I get:

```

[17179752.324000] Bluetooth: L2CAP socket layer initialized
[17179752.884000] Bluetooth: RFCOMM socket layer initialized
[17179752.884000] Bluetooth: RFCOMM TTY layer initialized
[17179752.884000] Bluetooth: RFCOMM ver 1.7
[17179837.216000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179837.216000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4330, sector=4327
[17179837.216000] ide: failed opcode was: unknown
[17179837.216000] end_request: I/O error, dev hda, sector 4327
[17179837.216000] JBD: IO error reading journal superblock
[17179837.216000] EXT3-fs: error loading journal.

```

Any ideas?  I really need to get this data off the drive, it's a website I was working on for a client, and I hadn't backed it up yet.

---

### Post by st33med on 2007-06-18
When loading into GRUB, try the memtest thing and tell us what's wrong.

Also, the read-write permissions could be screwed up, but not likely. Someone else can elp with that.

---

### Post by st33med on 2007-06-18
Also try this command in the LIVECD:
```
smartctl -a
```

This will tell us what's wrong.

EDIT: WHOOPS! You have to download a Cd to do this. [Download this]("http://www.inside-security.de/download_en.html"), burn it, then boot off it and type the command above.

---

### Post by TheDewAddict on 2007-06-18
> **st33med said:**
> When loading into GRUB, try the memtest thing and tell us what's wrong.

Also, the read-write permissions could be screwed up, but not likely. Someone else can elp with that.

Here are the results from memtest.  It ran once, and appears to be re-running itself.

```

L1 Cache:   128k    8589MB/s
L2 Cache:   256k    2631MB/s
Memory      512M     430MB/s
Chipset       AMD 761 (ECC: Disabled)

Cached:     512M
RsvdMem:    76k
MemMap:   e820-Std
Cache:       on
ECC:          off
Test:         Std
Pass:        1

```

---

### Post by st33med on 2007-06-18
Well, try the thing I mentioned above.

EDIT: Oh yeah, I'm sorry, that memtest is for the flash memory. So you can stop it. Again, sorry!

---

### Post by TheDewAddict on 2007-06-18
OK, I did:

```

smartctl -a /dev/hda

```

and I got:

```

Model Family:        Maxtor DiamondMax Plus 9 Family
Device Model:        Maxtor 6Y08OPO
Serial Number:       Y2CX5VHE
Firmware version:  YAR41BWO
User Capacity:       81,964,302,336 bytes
Device is:                In smartctl database
ATA version is:       7
ATA Standard is:    ATA/ATAPI-7 T13 1532D revision 0
SMART support is:  Available
SMART support is:  disabled

```

---

### Post by TheDewAddict on 2007-06-19
bump

Any ideas?  I really need to get the files off my drive.

---

