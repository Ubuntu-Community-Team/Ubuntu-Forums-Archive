---
title: "Partitions"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by skale on 2006-06-13
I only discovered what a "partition" was today, after I wiped the hard disk.

Anyway, it seems that you set the disk so that half is used for windows and the other half for linux, or whatever proportion you like. So here's my question:

Is it possible for one operating system to access the other partition and use files from it? Can there be files that both systems can access? How do you do it?

---

### Post by JanVH on 2006-06-13
[QUOTE=skale]I only discovered what a "partition" was today, after I wiped the hard disk.

Anyway, it seems that you set the disk so that half is used for windows and the other half for linux, or whatever proportion you like. So here's my question:

Is it possible for one operating system to access the other partition and use files from it? Can there be files that both systems can access? How do you do it?[/QUOTE]

If your Windows is XP, the filesystem used on the WinXP-partition is probably a NTFS-filesystem. Out of Ubuntu, you can automatically acces this files, but you can't write to them. You can't edit them either, thus.

The filesystem for Ubuntu is probably going to be ext3. You can't acces this from WinXP when you don't install an extra program.

If you want to write and read files from WinXP and Linux, the best thing to do is creating a third partition with the FAT32-filesystem. It's the older Windows and DOS-filesystem and is well supported by Linux.

---

### Post by anaconda on 2006-06-13
Or you coud install
[http://www.fs-driver.org/](http://www.fs-driver.org/)
to your windows XP, so that you can access read/write your linux partition (ext3) from windows

Ubuntu can read from ntfs partitions

---

### Post by The Cosmic Hobo on 2006-06-13
[QUOTE=skale]I only discovered what a "partition" was today, after I wiped the hard disk.[/QUOTE]
We should start a club for this - when I first installed Linux on the very first desktop PC I owned, way back in... ooh, 1999 or 2000 (before broadband internet became popular and affordable... I got the install CD off a magazine cover!), I had no idea what partitions were.
When the installer asked if I wanted to make partitions on my hard disk, I typed N - yep, command-line installer... bet you don't see many of those any more! Anyhow, when I found out that most of my hardware wouldn't work right, I decided to just uninstall it and go back to Windows.

... oops ... nothing on the hard disk but Linux!

So we've both learned the hard way. Hope you don't feel too bad about it! :)

---

### Post by skale on 2006-06-13
Thanks! 

And is there a program to edit "NTFS" files with Linux?

And, How much space do I need to allot each system? ( I have 40GB to play with)

---

### Post by RRS on 2006-06-13
There are a couple programs that allow writing and editing in NTFS from Linux but there still somewhat experimental and not always reliable.

My second computer has a 40g drive and Set up windows and Ubuntu with 15g each and created a 10g Fat32 partition for sharing.

Both Linux and Windows can read, write, and edit anything in Fat32 so it's the safest and most convenient way to share data between systems.
[URL="http://users.bigpond.net.au/hermanzone/index.htm"]
This site[/URL] has very good instructions for partitoning and installation, including the various options.

---

