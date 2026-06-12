---
title: "Lost all my data.."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-12
I have an external HDD (320GiB SATA).. I had just about 140MiB free on it. I tried to copy about 29MiB of mp3s to it.. after 3-4 seconds, the copy froze, and I got a dialog "Cannot copy Nickelback-Hero.mp3, the file doesnot exist'. So I just pressed Cancel and pressed the Back button on the HDD's Nautilus Window, but it refused to open. So I ejected the disk and re-mounted it. On an attempt to do so, it showed "Cannot mount volume. Data may be corrupt."
My HDD is in NTFS partition. I priorly once posted a problem that I couldn't access my NTFS HDD thru any Windows box (It told access denied), but worked absolutely fine in Gutsy (strange).. So I had to delete the partition through Windows Disk Management, losing 297GiB of my data.. Does ntfs-3g have similar bugs that it screws up the FS when it is almost full?

---

### Post by glennric on 2008-03-12
It is possible that ntfs-3g can mess up an NTFS partition.  First though, when you say you ejected the disk, how did you do that?  Did you unmount the partitions on the disk first, or just manually pop the disk out of the machine?

---

### Post by sayakb on 2008-03-12
> **glennric said:**
> It is possible that ntfs-3g can mess up an NTFS partition.  First though, when you say you ejected the disk, how did you do that?  Did you unmount the partitions on the disk first, or just manually pop the disk out of the machine?

I unmounted it.. I had banshee on, I exited it and unmounted the disk quite normally. But it just refused to mount again..

---

### Post by glennric on 2008-03-12
Can you boot to windows?  If so check the disk from windows.

---

### Post by Joeb454 on 2008-03-12
Looking at your sig, you may need to find a Windows machine to test the disk on :(

---

### Post by sfink16 on 2008-03-12
I accidentally formatted my hard drive when installing Ubuntu (didn't see the re-format box checked).  I lost all my windows XP OS along with all my data (lots of images from my cameras).

Fortunately, I found (and used) software called Active@Delete Pro 5.5 to recover almost all my data.  The software boots up in a small Vista OS with Undelete GUI to select from.  It works well!  The demo version allows recover of small data (56k).

For $50 (?), its' well worth it!

Steve

---

### Post by Joeb454 on 2008-03-12
> **sfink16 said:**
> The software boots up in a small Vista OS with Undelete GUI to select from.

Heh....I never knew there was such a thing as a small Vista OS :p 15Gb is a lot of space...

Anyway, might be worth looking into :)

---

