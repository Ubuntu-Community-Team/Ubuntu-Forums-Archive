---
title: "Changing a disk from ntfs to something else"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by mgilb666 on 2007-09-28
I installed Ubuntu on a system with two disks.  The system used to have XP on it.  The installation went fine and the system disk is ok.  The second disk is of type ntfs and is read only.  I want to re-format the disk to another type and blow away all of the data on it.  I've tried several mount options and nothing works.  

How do I do this?  What type is best with Ubuntu ext3 or?

It's been years since I did any work on UNIX stuff so a little rusty.

Thanks,

Mike G.

---

### Post by Malibu Illusion on 2007-09-28
If you unmount all volumes of the disk then execute Gparted, you should be able to select the device and format it as per your requirements.

Type this into a command line:

```
gparted
```

---

### Post by wormser on 2007-09-28
Gparted is an easy way to reformat a drive.

```
sudo gparted
```

I am unsure if drive needs to be unmounted.  If there is a problem you should be able to right click on the drive and click Unmount.  I believe that Reiserfs is the best but ext3 should be fine.

---

### Post by bruce89 on 2007-09-28
The best way is to use the [ GParted CD]("http://gparted.sourceforge.net/livecd.php"), it means you don't have to unmount anything.

---

### Post by Malibu Illusion on 2007-09-28
I'd say it was fairly overkill to download and burn the Gparted LiveCD when all he wishes to do is make partition changes on a drive that is not in use anyway, save for potentially having it mounted.

Just perform the operation within Ubuntu itself; it's not like unmounting isn't as easy as right clicking and selecting "unmount."

---

### Post by mandrill on 2007-09-28
suggestion only - if you are reading and writing in a mixed OS LAN, ie windows/linux, fat32 works for both.......

---

