---
title: "unmount a hard drive"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by JohnN on 2006-06-14
Does anybody know the command to unmount a hard drive to run fsck in he terminal outisde of the XWindow (when the XWindow isn't running?)

I need to run fsck.

---

### Post by David_T on 2006-06-14
Try umount.

---

### Post by yager on 2006-06-14
sudo umount /dev/xxxxx since you have to be root to unmount any device that was mounted on startup.

---

### Post by JohnN on 2006-06-14
"unmount" didn't work, anybody else know what commands I can use to unmount my hard drive to run fsck on it?

---

### Post by David_T on 2006-06-14
that's umount, not unmount.  type "man umount"

---

### Post by Sutekh on 2006-06-14
Its actually umount, not u**n**mount.

The other consideration is that you can't unmount a hard drive that is in use. Is this drive that you need to unmount your only drive, and thus the one that Ubuntu is running on?

---

### Post by JohnN on 2006-06-14
Yes, its my only hard drive that I need to run fsck on, and what is the command to use inside of umount?

---

### Post by JohnN on 2006-06-14
Yes, its my only hard drive that I need to run fsck on, and what is the command to use inside of umount?

---

### Post by yager on 2006-06-15
Sutekh was trying to ask if the drive you want to run fsck on is the same hard drive that you are running Ubuntu from right now.  Do you only have 1 hard drive in the computer that is formatted for use with Linux?  If this is the case, you need to boot your computer from  your Ubuntu Install/Live CD so that /dev/hda1 or /dev/sda1 or whatever device Ubuntu is on is not mounted as the root operating system.  This way you don't have to mess with umount.

After you get to the desktop on the Live CD, open a terminal window and enter
```
sudo fsck /dev/xxxx
```
Change the /dev/xxxx to the correct item for your computer.

In the event you are trying to repair some partition other than the root partition, do the following.
```
sudo umount /dev/xxxx 'the xxxx is the device to fix
sudo fsck -N /dev/xxxx 'this will show what would be done to your drive to fix it.
sudo fsck /dev/xxxxx 'will now make all of the listed changes above.  
```
Only do the last line if you do not see any serious risk from the above report.  The fix may be more drastic then you want before pulling off you data files.

---

### Post by Sutekh on 2006-06-15
Ok and which partition, do you need to run fsck on? Is it your main Ubuntu partition (the / partition) or another partition? This is what I'm getting at, if you need to fsck your main Ubuntu partition, you won't be able to whilst in Ubuntu.

You will need to either use a LiveCD to perform this, or start Ubuntu in recovery mode from the GRUB menu (I think)

If you need to fsck a different partition, not your main Ubuntu one, then to unmount a partition you need to use, for example
```
sudo umount /dev/hda2
``` Where /dev/hda2 is the partition to be unmounted. Then you can run fsck on the partition.

Edit: OK, wow. I really should have refreshed the page! Follow what yager has posted

---

