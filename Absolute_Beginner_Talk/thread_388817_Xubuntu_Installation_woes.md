---
title: "Xubuntu Installation woes"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-03-19
I've been trying to install Xubuntu again, but now It is taking forever to start installing. It's been having a problem with the partition manager, as in the partition manager is not loading.

 Can anyone help?

---

### Post by ZeroWing on 2007-03-20
No, I'm not impatient...

---

### Post by partsdale on 2007-03-20
you said to install 'again'... is the filesystem of the hard drive you are installing onto already formatted ext3?
there are several variables that could cause what you are describing...

---

### Post by ZeroWing on 2007-03-20
No. Last time I uninstalled, Windows XP was scrubbed, so I had to format my HD and reinstall everything.

 Has my beautiful Hard drive croaked? :(

---

### Post by partsdale on 2007-03-20
that wouldn't be my first guess... so did you say you reformatted the hard drive proor to the install attempt? if so, what file system was it formatted to?

---

### Post by ZeroWing on 2007-03-20
It was an automatic format and install. HP System Recovery made two partitions: one for WIndows XP, NTFS format, and the other for System Recovery itself, in FAT32 format.

 By the way, the partitioner goes as far as letting me select the amount of free space to use.

 Could it be because The HDD is fragmented? I haven't ran a defrag since I reinstalled Windows(about three weeks).

 [EDIT] Yay! Thirty posts of stupid![/EDIT]

---

### Post by ZeroWing on 2007-03-20
Come on guys...

 Did a defrag, but nothin' doin'.

 *help.*

---

### Post by ZeroWing on 2007-03-20
Please guys, I could really use the help!

 I like Xubuntu!

---

### Post by ZeroWing on 2007-03-21
I tried to install Kubuntu too, and it does the same thing. Figured it would.

---

### Post by zvacet on 2007-03-21
Selwct manualy and see what will heppened.If everything goes O.K. you should see all your partitions.Partition your free space like this:
1.root / =5 or more GB
2.home =rest of free space exept
3.swap =2xram
All your Ubuntu partitions need to be in ext3 format.

---

### Post by ZeroWing on 2007-03-21
I don't want to try to partition my PC manually, because I think that I might *really* mess something up.

 Is there any other way I could do this?

---

### Post by ZeroWing on 2007-03-21
I've found that I could install Xubuntu by using the largest continuous free space, but I'm afraid that means that I will not have any free space for my Windows partition...

---

### Post by mahy on 2007-03-21
Have you tried installing Xubuntu using the Alternate installation CD?

---

### Post by ZeroWing on 2007-03-21
> **mahy said:**
> Have you tried installing Xubuntu using the Alternate installation CD?

 I've been looking for that, but I can't seem to find it.

---

### Post by mahy on 2007-03-21
> **ZeroWing said:**
> I've been looking for that, but I can't seem to find it.

The ISO file: [http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso)

The torrent file: [http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso.torrent](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/6.10/release/xubuntu-6.10-alternate-i386.iso.torrent)

Maybe i'm too paranoid, but i don't trust those graphical installers and i've only ever installed any Ubuntu using the alternate installation.

---

