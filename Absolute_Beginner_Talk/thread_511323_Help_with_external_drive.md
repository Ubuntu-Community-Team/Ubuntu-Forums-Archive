---
title: "Help with external drive"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by ljpm on 2007-07-27
Hi All,

I have a little problem that I hope someone can help with. My wife has an 80Gb USB acomdata external hard drive which she uses on a Mac. Last night her computer crashed and since then she has been unable to access the drive (won't mount). I plugged it into my computer (Feisty) and it showed up on the file browser and correctly displayed the size of the drive but the drive wouldn't mount. If I click on the drive I get an error box which states "cannot mount volume". Clicking on the details button of the error box gives "mount: not a directory" 

fdisk -l gives 
```
Disk /dev/sde: 80.0 GB, 80026361856 bytes
81 heads, 63 sectors/track, 30629 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30630    78150712+  af  Unknown

```

I really can't format the drive as it contains family pictures that are irreplaceable. 

ps.    I know that this is not a Ubuntu problem but I didn't know where else to ask.


Thanks in advance.

---

### Post by wolfen69 on 2007-07-27
i'm not sure, but it could be because macs use a different file system.

---

### Post by Rocket2DMn on 2007-07-27
> **wolfen69 said:**
> i'm not sure, but it could be because macs use a different file system.

Yeah, but what file system?  I thought most people could read their Apple drives in Ubuntu.  Perhaps that disk is also corrupted?

If there are any Apple users out there, please give input.

---

### Post by Ek0nomik on 2007-07-27
> **Rocket2DMn said:**
> Yeah, but what file system?  I thought most people could read their Apple drives in Ubuntu.  Perhaps that disk is also corrupted?

If there are any Apple users out there, please give input.

Don't MAC's use HFS Plus file systems?

I would try this:

```
sudo mkdir /media/macexternal
sudo mount -t hfs dev/sde1 /media/macexternal
```

---

### Post by ljpm on 2007-07-27
> **Ek0nomik said:**
> Don't MAC's use HFS Plus file systems?

I would try this:

```
sudo mkdir /media/macexternal
sudo mount -t hfs dev/sde1 /media/macexternal
```

Thanks but I get this
```
mount: special device dev/sde1 does not exist

```

---

### Post by Rocket2DMn on 2007-07-27
[http://packages.ubuntu.com/feisty/otherosfs/hfsplus](http://packages.ubuntu.com/feisty/otherosfs/hfsplus)
Installing that should give you the ability to read the file system, assuming it is actually HFS+

---

### Post by Ek0nomik on 2007-07-27
Two reads:

[http://ubuntuforums.org/showthread.php?t=92141](http://ubuntuforums.org/showthread.php?t=92141)

[http://ubuntuforums.org/showthread.php?t=98286](http://ubuntuforums.org/showthread.php?t=98286)

---

### Post by coffeecat on 2007-07-27
If that external HD was purchased already formatted and your wife hasn't reformatted it with her Apple Mac, it was probably formatted as FAT32. Macs can read and write to FAT32 drives, so manufacturers usually go for the 'safe' (read most widely readable) option of fat32. More or less the same for USB flash drives. I've just plugged one into this Ubuntu box and Gparted reports it as FAT16.

Have you tried plugging it into a Windows box? If it's a FAT formatted drive Windows might just make something of it.

---

### Post by KyleBrandt on 2007-07-27
sudo mount -t hfs dev/sde1 /media/macexternal

I think should be:

sudo mount -t hfs **/**dev/sde1 /media/macexternal

Notice the "/" before dev

---

### Post by ljpm on 2007-07-27
Thanks all.

It seems the file structure got mangled some how. My wife as able to repair it with a disk utility program. We probably lost some files I just hope we haven't lost anything important. 


ps. This is the second time in 2 years we have had trouble with the acomdata drive. The first time it was only 1 month old and we had to send it in, something about the board frying everything. I will never buy acomdata again.

---

### Post by Rocket2DMn on 2007-07-27
Maybe now would be a good time to invest in another hard drive and use it to back this one up.  Then you can keep both around, so long as you keep good backups - nothing like a little redundancy.

---

