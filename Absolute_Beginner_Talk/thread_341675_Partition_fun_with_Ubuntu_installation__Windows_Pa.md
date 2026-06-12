---
title: "Partition fun with Ubuntu installation / Windows Partition Magic"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by deadimp on 2007-01-19
[Background on my dilemma. Skip it if need be]
I've recently installed Ubuntu as a partition on my primary hard drive (C:, /dev/hda), and it's been working well so far. It's neighbor is Windows XP, and it's still working (it's what I'm using right now).
However, before I had ran the setup for Ubuntu (off of the Live CD), I had gone into Partition Magic and created a partition for a new operating system. Now that I look back on it, that wasn't too grand of an idea. I allocated ~7g or so, not sure on the exact estimate.
When I ran the Ubuntu setup, I ran into the partition management section, where it prompted me on how/where to install the OS. Since I had no idea what I was doing (I'm just now accustoming myself to partitioning), I had it make the partition for me, and I was only allowed to select > ~14g for the partition by the slider bar.

[The Problem]
It took a while, but it worked, and the system installed, and everything was simply fine and peachy. However, when I reverted to Windows and ran Partition Magic to resize some of my partitions, it told me that my table was corrupt (LBA address, and the like).
When I went back to Ubuntu and ran "fdisk -l" (or -p?), I received a printout on four partitions:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2198    17655403+   7  HPFS/NTFS
/dev/hda2            2199        4772    20675655   83  Linux
/dev/hda3            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

```
[Gonna add to this when I go to Ubuntu]
Problem is, partition 3 (/dev/hda3) and 5 (/dev/hda5) overlap (the cylinder/sector boundaries are nearly the same). When I run cfdisk (or whatever the name is for the 'user-friendly' version of fdisk), I get a printout on three partitions, and it doesn't read the 3rd at all. This is bad, in that I can't select it to remove.
So I execute 'parted', and mess around in that some. In this, I try to remove the partition, like so:
(parted) rm 3
However, it tells me that /dev/hda3 is mounted. So I execute:
$ umount /dev/hda3
It tells me that this wasn't even mounted to begin with. It isn't even listed in "mount" or "/etc/fstab".
I go back to parted, execute the command again. Same error.

I've read an article on this, and in it the user (Arsgeek) said he fixed the problem by turning LBA on /dev/hda off, running Partition Magic, rebooting, turning LBA back on, and running Partition Magic once more. However, it seems quite risky (more than what I'm doing right now), since I fear Partition Magic might think that its partition is correct, and will remove the SWAP partition.

So now, I can't remove the partition by Ubuntu since it thinks the partition is still mounted, and I fear to remove it by PM because it might screw with Ubuntu.
I'm going to try and boot with Ranish Partition Manager, and see if that reads partition #3, and then remove it. But right now, I've got a floppy stuck in the drive, and it isn't reading it (which is good, since I can boot normally).

Any suggestions on what other courses of action I can take?

NOTE: I'm currently writing this in Windows. I'm gonna reboot to Ubuntu to add the other details.
> EDIT: Details added.

---

### Post by Cobikegeek on 2007-01-19
I would suggest booting the Ubuntu live CD and doing your repartioning from there.  That way none of your partitions are mounted and parted or gparted should work.  I'm not exactly sure where you are trying to get, but you could probably delete the ext2 partition and then expand the ext3 partition up to the sectors where swap starts.  As always back up any data you wouldn't want to lose before partitioning.

---

### Post by tonyr1988 on 2007-01-19
Yes, try the LiveCD - it shouldn't mount a single partition, so you can manipulate what you want.

If, for whatever reason, your computer has problems with the Ubuntu LiveCD (if it doesn't run, or runs slowly, etc.), there's also a LiveCD that only has GParted on it:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I've got a copy, and I've used it a few times - it's a pretty good resource.

If a LiveCD doesn't work, then PartitionMagic has done something evil (you may have to resort to the LBA solution). Helpful hint for the future: don't use PartitionMagic for Linux file systems - it does a horrible job and there are FOSS alternatives (ex GParted :)).

---

### Post by Sef on 2007-01-19
> I had gone into Partition Magic and created a partition for a new operating system.

Partition Magic is not recommended for use with Linux.  It and Linux don't get along too well.  As has been previously mentioned, use [GParted]("http://gparted.sourceforge.net") or the Ubutnu Live CD, which has an older striped down version of Gparted on it.

---

### Post by deadimp on 2007-01-19
Well, I'll go ahead and do that.
When I tried to use gparted before on the Live CD, it began to throw errors that this could potentially screw over my system, and wouldn't allow me to use it. However, I hadn't tried parted, fdisk, etc.

---

### Post by deadimp on 2007-01-19
Ah crap. I've screwed over my partition. Everything seems to be working fine, but the boundaries on my partitions (the two remaining) are all jacked up because I had decided to allow Partition Magic to 'fix' the error. Bad idea.
Now I need to figure out how to reset the boundaries, based on what I had posted here, with fdisk.

---

### Post by deadimp on 2007-01-21
Well, this is more or less just crap that I'm typing...
I've fixed my partition, for the main part, after about a day or two of manually screwing around with my the tables, using fdisk, cfdisk, sfdisk, parted, and gparted on my Ubuntu LiveCD. Good Jesus, it was some gawd-awful fun.

My main error was, as with any other ignorant noob, not proprely backing-up my partition. Dunno why I didn't, just wasn't... thinking. At all.
My other problem was that I had thought that my drive (/dev/hda) had 16 heads/cylinder, and I gathered this geometry from fdisk. Ends up, fdisk just decided this on its own. Each time I tried to redo my partition table, I was using this incorrect geometry (16h/c), and the boundaries were obviously not correct. This came to my realization each and every time I rebooted my computer without the LiveCD, in that GRUB, in Stage 1.5, gave me Erro 17, which meant the partition was read but somehow incorrect.
When running a diagnostic with sfdisk, I received information that I had *255* heads/cylinder. What a grand moment that was. So when I re-did my calculations (simple multiplication, yet so frustrating), I got the ~true numbers.
As for truly screwing around with my partition, I never found a format I was particularly comfortably, and resorting to dumping/inputting partition table data with sfdisk (plus, this allows me to back up information more easily).
In the end, GRUB stopped "spewing venom in my eyes" and allowed me to boot. When I got to Ubuntu, I got around to 30% loaded, and then it gave me an error in fsck. There's a difference between the file system's size and the partition's description on it by around 4 blocks. Gonna play around with the size (after backing-up important data this time), see if I can fix this. Problem is, I can't boot Ubuntu 'cause there's another error, saying that my root filesystem had a certain inconsistency in them. Don't know what to do about this (I'll repost on it later). Plus, I need to re-add my swap partition -- or even better, just reinstall Ubuntu altogether.
As for Windows, everything seems to be working like a charm (aside from nt2002.exe somehow being removed). I'm using it now to post this. Partition Magic, though, is still complaining, and it can continue to do so (gparted seems a lot better to me right now).

Good God I hate partitioning.

---

