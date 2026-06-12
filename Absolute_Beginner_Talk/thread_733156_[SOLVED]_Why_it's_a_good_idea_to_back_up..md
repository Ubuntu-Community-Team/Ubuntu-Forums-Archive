---
title: "[SOLVED] Why it's a good idea to back up."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by drewster1829 on 2008-03-23
My Toshiba Satellite M55-S331 was giving a "Resource Conflict - PCI Network Card on Motherboard" error at POST, and I was trying to troubleshoot it.  The source of the problem seemed to be the built-in WiFi card (removing it was the only way to prevent the message at boot; turning it off from the switch on front did not remove the message at boot).  I tried re-installing it, thinking it might have been loose, but the message returned with the card back in place.

I did just install a 1GB DDR SODIMM a couple days ago, but removing it also did not remove the message.

I tried resetting the oh so basic BIOS to default values, with no change.  Then, I thought "Maybe the Toshiba Recovery disk has the old BIOS on it" (thinking I might have corrupted the BIOS, but this seems unlikely.  I tried to install a Windows based BIOS update in WINE before I was getting the message, but it failed with some error or another.).

I popped in the disk (after changing the boot order so it would boot the recovery disk), and it started to load, then rebooted itself, then loaded the Recovery disk, and *then* (this is when the cussing starts :)) immediately started restoring the laptop to its factory default settings, including repartitioning and copying files; it gave me no warning, no prompt, no nothing.  I immediately hit the CD drive button and simultaneously held the power button, took the CD out, and threw it across the room in a rage.:mad:

So now, it boots, still gives me the WiFi card error at POST, and says "GRUB loading...", then goes into a reboot loop.  I stuck in a 7.04 LiveCD I had lying around (I **HAD** 7.10), to find an NTFS partition and a few Windows files on the HD of the laptop.

The worst part is, I have an empty 80 GB external drive formatted ext3 that's hooked up to the laptop (He he, a little late), the exact size of the drive in the laptop.  Can I dd the data over and restore my data files somehow?  The data is still on the drive, but with the partition table overwritten, I think I'm SOL.  :(  I'm going to destroy that system restore disk in a very slow and very painful manner.  

@#$&(*!@&!!!

---

### Post by louieb on 2008-03-23
[SystemRescueCd]("http://www.sysresccd.org/Main_Page") has a program called **testdisk** it may be able to rebuild your partition table. Another tool on the disk is GNU-parted it may be able to rebuild your partition table too.

---

### Post by drewster1829 on 2008-03-23
Thanks!  I'll give it a shot, but let me make it clear that the #$&*ing recovery CD didn't just delete the old partition, it overwrote it with an NTFS one.  However, even though there are a couple (incomplete) Windows files, but the drive shows the same used space as before the snafu (about 40+ GB used).  This seems to indicate (to me) that maybe the whole ext partition table wasn't cooked.

I appreciate the utilities, though, I'll certainly try them out.  Thanks again :)

---

### Post by drewster1829 on 2008-03-23
I might try *foremost* if I can't fix it with sysreccd, but that will be a last resort, since I'm sure I'll miss files of some type that I can't remember in order to add to foremost.conf.  Keep your fingers crossed!

---

### Post by drewster1829 on 2008-03-25
Well, I found another file recovery utility ([PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")), and ended up having to use it after trying to repair the partition table failed.  It is advertised to recognize over 100 file types, but it turned the entire disk into files (onto my external drive).  Most of it was garbage, almost all unreadable zip files, and lots of 'txt' files which were chunks of plain text from any kind of file imaginable.

It did manage to recover some images, but they were almost all thumbnails.  The few large ones it attempted to recover were corrupted, so I think it might have had trouble if they were fragmented, or even if they were larger than a single block in size.

Oh well.  I'll learn my lesson and be sure to back up **OFTEN**!  I didn't lose much data, as most of it was backed up onto a 500 GB external drive, but I'm mostly angry about losing my system configuration.  It'll take forever to rebuild it from scratch!  I guess this is a good excuse to try out the Beta of Hardy Heron, though. :)

---

### Post by UltraAnders on 2008-03-30
That's a terrible recovery disc. Possibly a bit late, but "Recovery is Possible" saved my a*s on a previous failed attempt to install Linux. I think I only managed to delete all the partitions rather than formatting one, but might be worth a try!
[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

What do people use as backup software in Ubuntu?

---

### Post by Tews on 2008-03-30
Sorry that you're having such a hard time restoring your files.  I strongly recommend using Quick-Start.  Designed specifically for Ubuntu, to restore your system to a previously backed up state.  Think of it as System Restore.  You can schedule backups for daily, weekly or monthly.  You can get it here ===> [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

---

### Post by drewster1829 on 2008-05-30
> **Tews said:**
> Sorry that you're having such a hard time restoring your files.  I strongly recommend using Quick-Start.  Designed specifically for Ubuntu, to restore your system to a previously backed up state.  Think of it as System Restore.  You can schedule backups for daily, weekly or monthly.  You can get it here ===> [http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

Thanks!

---

