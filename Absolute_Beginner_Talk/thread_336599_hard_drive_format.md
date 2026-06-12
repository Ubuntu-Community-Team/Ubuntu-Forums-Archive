---
title: "hard drive format?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by DavidOhio on 2007-01-11
I started to do the install for 6.10 when I noticed a number of ways to format the drive. This is the way I plan to set it up. Is this the right way to do it?    Thanks David

/            10gb               primary partition-filesys-ext3
swap      1152mb              "            "      -filesys-linux swap
/home     (the rest)           "            "      -filesys-ext3

AthlonXP 1.53GHz
768 ram
80gb Winxp Sp2 (home)
80gb will be Ubuntu
GeForce 6600 AGP 256mb

---

### Post by meng on 2007-01-11
Looks like an excellent (and simple) partitioning plan!

---

### Post by Sef on 2007-01-11
> / 10gb primary partition-filesys-ext3
swap 1152mb " " -filesys-linux swap
/home (the rest) " " -filesys-ext3

AthlonXP 1.53GHz
768 ram
[B]80gb Winxp Sp2 (home)
80gb will be Ubuntu[/B]
GeForce 6600 AGP 256mb

Are you planning on dual booting Linux and XP or running just Linux?

---

### Post by DavidOhio on 2007-01-11
I'm going to duel boot.

---

### Post by tonyr1988 on 2007-01-11
Then you'll need to keep a partition for WinXP (probably NTFS) and shrink down your /home partition. Most people make a "shared" partition (usually FAT32, unless you have files >1GB)

You shouldn't need 80GB for Ubuntu (or WinXP) if you share files between the two (music, documents, photos, etc.)

On my laptop (where I was being generous), I have WinXP and Ubuntu 40GB a piece (and I install a bunch of programs), and it's more than enough. On my desktop, Ubuntu has it's own 15GB hard drive, and I'm far from filling even it up.

P.S. Make sure you defrag your Windows (even if WinXP says you don't need to) before you shrink the WinXP partition.

---

