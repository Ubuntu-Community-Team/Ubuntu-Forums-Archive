---
title: "Uninstall Ubuntu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by masonpitzel on 2007-11-25
Alright, so I've decided to install Ubuntu off my dual-boot XP computer.  It's basically a little too techy for my tastes, and I'm finding it sort of hard to work around the problems I'm having with it.  So I've decided to uninstall it.

Things of note:
1) I think I screwed up my dual-boot when I was installing Ubuntu.  This supposed GRUB Boot Menu never showed up after installation, and so Ubuntu automatically starts up when I power up my computer.  But XP is still on there somewhere (I hope -- I tried using this NTFS  Configuration Tool to access some of the songs, photos, etc. I have on my XP partition, and it basically told me that I don't have one).
2) I don't have any backups of my personal files on the XP partition!  Yes, I'm an idiot, I know.  So now I'm looking for ways to restore XP that don't begin with "Step 1: Wipe your drive!"

I hear this Super Grub Disk is the best option, but I have no clue what to do with it, especially since I may have screwed myself over XP-wise.

Any help would be great.

---

### Post by Taboo Mirage on 2007-11-25
Well, first and foremost if you could post the output of this command, it will tell us whether or not you still have your NTFS partition:

```
sudo fdisk -l
```

---

### Post by masonpitzel on 2007-11-25
Output is as follows:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19101   153428751   83  Linux
/dev/sda2           19102       19452     2819407+   5  Extended
/dev/sda5           19102       19452     2819376   82  Linux swap / Solaris
mason@mason-desktop:~$ 





I don't see the word "NTFS" in there, do you? :(

---

### Post by Taboo Mirage on 2007-11-25
Seems to me as though, during the Ubuntu installation process, you've gone ahead and told it to use the entire drive rather than configure partitions.  This essentially means you've overwritten your Windows data.

---

### Post by masonpitzel on 2007-11-25
...ooookay, so that's not good.

So, how do I get Ubuntu off my machine and put XP back on?

---

### Post by Taboo Mirage on 2007-11-25
You will need a disc capable of installing Windows XP.  From there, you can use the Windows partition manager to delete the other partitions and install XP again on its own.

You may want to consider checking out software such as [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) which may be able to recover the NTFS partition and retrieve some of your files.

Good luck.

---

