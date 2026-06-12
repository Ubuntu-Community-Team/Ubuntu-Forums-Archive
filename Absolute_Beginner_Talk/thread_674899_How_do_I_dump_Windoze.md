---
title: "How do I dump Windoze???"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-01-22
I am using Gutsy Gibbon 64-bit. I have a 320GB external SATA HDD. Yesterday, when I plugged it into my machine, I forgot to unmount it and forcefully turned my laptop off (by pressing the power button for 5 seconds). As a result, when I plugged in the HDD on my next reboot, it told me "Cannot mount Glade. Invalid mount point /media/sdb5" or something like that (I don't exactly remember). I tried to mount it by using force option:
root@Muzic-Jukebox:~# mount -t ntfs-3g /dev/sdb1 /media/Glade -o force

But it told me something like "Mount failed. Unmounting device Glade"

I plugged the HDD in a Windows machine, where it showed me a yellow triangle at the notification are indicating : "Corrupt files on / . Run chkdsk to correct this error". So I scanned the HDD using chkdsk which fixed it.. 

But this is not a solution. I just want to be independent from the Windows episodes.. wanna just get rid of Windows. How could I have solved my problem in Linux. I am a beginner and don't really have much knowledge about Linux, so please guide me :)

PS: I couldn't afford to lose data on my disk. So please tell me a way which doesn't involve formatting or deleting a partition.

---

### Post by Cypher on 2008-01-22
If you want to not use Windows to do any disk recovery, don't use NTFS as the filesystem. Using an EXT3 partition on a drive will allow Linux to recover it.

So backup the data on there, reformat it to EXT3 and put the data back.

---

### Post by sayakb on 2008-01-22
> **Cypher said:**
> If you want to not use Windows to do any disk recovery, don't use NTFS as the filesystem. Using an EXT3 partition on a drive will allow Linux to recover it.

So backup the data on there, reformat it to EXT3 and put the data back.

I would do that. But please explain how do I recover data on ext3 fs HDDs..

---

### Post by MonctonJohn on 2008-01-22
If the drive had been ext3 you could use fsck.ext3. Here is a link to the man page: [http://linux.about.com/od/commands/l/blcmdl8_fsckext.htm]("http://linux.about.com/od/commands/l/blcmdl8_fsckext.htm")

---

