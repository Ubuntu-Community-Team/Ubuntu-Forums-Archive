---
title: "removing hard drive from dual boot system"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by gj_clt on 2008-01-26
I have been dual booting XP and 7.10 for a month. Decided I don't need XP. I have two hard drives one XP one Linux. I want to physically remove the XP drive. As a total newbie I would like some advice as to how to do this - I'm thinking I'll have to edit Grub.

---

### Post by Norman Grahams on 2008-01-26
I think GParted (which you can use from the Live CD) might have a utility to sort that out, but I don't know.

If it's not too much hassle to back up your data and reconfigure your settings in Ubuntu, I suggest the easiest way is to backup, change the hard disks, and then reinstall Ubuntu - which will sort out the MBR (Master Boot Record) 

Presumably you know about 'master' and 'slave' stuff with jumpers when physically changing hard disk setup?

---

### Post by chewearn on 2008-01-26
Please post output of:
```
sudo fdisk -l
```

so that we know what is where in your harddisks.

---

### Post by cmnorton on 2008-01-26
If I remember correctly, the Windows and Linux boot images are found on the first primary hard-drive, so you would edit grub's config file under boot. 

After backing up the second drive, why not create an ext3 file system on it, a mount point, and have it mount each time you boot?

---

### Post by mikeyphi on 2008-01-26
> **gj_clt said:**
> I have been dual booting XP and 7.10 for a month. Decided I don't need XP. I have two hard drives one XP one Linux. I want to physically remove the XP drive. As a total newbie I would like some advice as to how to do this - I'm thinking I'll have to edit Grub.

Have a look at this guide: [https://help.ubuntu.com/community/GrubHowto?](https://help.ubuntu.com/community/GrubHowto?)

especially the section: Changing the Disk that Grub is installed to

You might want to change Grub before removing the other drive!!

---

### Post by jken146 on 2008-01-26
You'll want to remove the hard disk first, then follow these instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by gj_clt on 2008-01-26
Solved. Thanks for the replies. I looked at the various threads and as such a newbie I decided to simply remove the drive, change the jumper setting(thanks Norman) and reinstall. Doesn't actually take very long.

---

