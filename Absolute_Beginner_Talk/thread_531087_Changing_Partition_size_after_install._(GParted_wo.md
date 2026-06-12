---
title: "Changing Partition size after install. (GParted won't resize NTFS?)"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by pockets on 2007-08-21
Hi, I have Ubuntu + Windows on my Laptop both of which I use regularly. However, my soundcard (M-Audio Firewire 410) isn't supported in Ubuntu so I must now make my Windows partition bigger to accommodate all my music + movies. Problem is GParted says NTFS resizing isn't supported and I've heard that partition magic is unpredictable at best! Any suggestions?

Thanks in advance!

---

### Post by mikeyphi on 2007-08-21
> **pockets said:**
> Hi, I have Ubuntu + Windows on my Laptop both of which I use regularly. However, my soundcard (M-Audio Firewire 410) isn't supported in Ubuntu so I must now make my Windows partition bigger to accommodate all my music + movies. Problem is GParted says NTFS resizing isn't supported and I've heard that partition magic is unpredictable at best! Any suggestions?

Thanks in advance!

Make a separate fat32 partition, this will be accessible by both OS's

---

### Post by vanadium on 2007-08-21
Sure ntfs resizing is not supported by gparted? Sure you're audio card is not supported by Linux? You could also go the other way round and access the ext3 system from within windows. I know there are drivers for that, but I have no experience myself.

---

### Post by Terl on 2007-08-21
I agree with Mikey - make another partition.  If you make it FAT32 as suggested both O/S's can use it easily.  It is the cleanest, easiest solution, IMHO.

---

### Post by bumanie on 2007-08-21
You don't mention which version of windows you are using. If it happens to be vista, gparted does not support vista at this pont in time.

---

### Post by freebeer on 2007-08-21
I've resized NTFS partitions (non-Vista) before with gparted.  The "trick" is to unmount the partition first before you try.  It's not obvious, but that's what I had to do and it worked just fine.

---

### Post by Teamgeist on 2007-08-21
A good way of doing this is using the gparted-LiveCD.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

