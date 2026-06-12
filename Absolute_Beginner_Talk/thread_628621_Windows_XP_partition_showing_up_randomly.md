---
title: "Windows XP partition showing up randomly"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by gofeddy on 2007-12-01
Hello,
         I have installed Ubuntu 7.10 on my system along with Windows XP which was pre-installed. Now, whenever I enter into my Ubuntu OS, my Windows partition(named sda1) doesn't show up or it cannot be accessed at all times. 
As an example, when I restart my system, I am able to access Windows. Then, during the next system start, it may not be accessible again. So, this random accessibility of Windows on Ubuntu is bugging me. So, why doesn't the Windows partition show up or be accessible every time I start up Ubuntu or Why is this random behavior?

---

### Post by stoodleysnow on 2007-12-01
Could your hard drive be failing? If the MBR is becoming a bad sector, it could cause that. Or it may be a corrupt Grub install.

---

### Post by gofeddy on 2007-12-01
I feel I have a virus or some malicious program on my Windows OS. Could that be causing this problem?
I have installed my Ubuntu safely specifying all my GRUB options correctly. Maybe the MBR has a bad sector, I don't know? So, what do I do to correct this problem?

---

### Post by MrFSL on 2007-12-01
Is this an ntfs partition?

If it isn't released correctly by Windows, or is scheduled for a check disk etc.. it will cause mount issues.

To troubleshoot you can try to manually mount the drive from the command line:
```
mount -t ntfs-3g /dev/sda2 /media/sda2
```

where **/dev/sda2** is the address to the block device representing your windows partition -- and** /media/sda2** is the path to the directory where you will be mounting the drive.

---

### Post by gofeddy on 2007-12-02
I guess, I have to use this mount option for now whenever I am not able to access my Windows partition. However, I'll try to check my Windows system for viruses, etc and also perform some hard disk error checking for bad clusters and hopefully post a successful reply.=P~

---

