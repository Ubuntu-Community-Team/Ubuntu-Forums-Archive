---
title: "Another GRUB Error 17"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by zchenyu on 2007-12-25
Ok, I've had Ubuntu for a while (couple months) now and I decided that I don't want Windows anymore. Previously, I dual-booted Windows and Ubuntu, just in case I decided to keep one of them. So I booted up the Ubuntu Live CD and went to the Partition Editor. It took a while and crashed the Partition Editor a few times (when swapping off and unmounting stuff), but I eventually got the hard disk the way I wanted. Then I restarted the computer and then GRUB gave the error 17.

Previous Hard Disk:
hda 1 - ntfs (Windows)
hda 2 - fat32? not sure (Windows I think (not sure why this is here, but I think this partition has something to do with System Restore))
hda 4 - extended
[LIST][*]hda 5 - ext3 (Ubuntu)
[*]hda 6 - linux-swap (swap space for hda5)
[*]hda 7 - linux-swap (swap for a previous installation of Ubuntu, didn't remove previously)
[/LIST]

Now:
hda 4 - extended
[LIST][*]hda 5 - ext3 (Ubuntu)
[*]hda 6 - linux-swap (Ubuntu)
[/LIST]

Any ideas?

---

### Post by logos34 on 2007-12-25
try reinstalling grub from live cd:

sudo grub

> find /boot/grub/stage1
(should show '(hd0,4)', i.e. hda5)

> root (hd0,4)
> setup (hd0)
> quit

---

### Post by zchenyu on 2007-12-25
Ok, I did what you said and now I'm one step closer. GRUB boots properly now, however when I select Ubuntu to boot, it gives me yet another Error 17, cannot mount partition. Any ideas on how to fix this?

---

### Post by logos34 on 2007-12-25
what's 

**sudo fdisk -l**

show?

---

### Post by zchenyu on 2007-12-25
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda4               1       24321   195358401    5  Extended
/dev/hda5   *           1       24043   193125334+  83  Linux
/dev/hda6           24044       24321     2233003+  82  Linux swap / Solaris

```

---

### Post by logos34 on 2007-12-25
run a filesystem check on it from live cd:

sudo fsck /dev/hda5

or

sudo e2fsck -y -f -v /dev/hda5

(root should NOT be mounted, so don't click on it in nautilus)

---

### Post by zchenyu on 2007-12-25
Thanks for all your help Logos, my friend figured it out. The problem was that the info in /boot/grub/menu.lst was inaccurate. I basically changed all the "(hd0,5)" to "(hd0,4)"

Then I edited fstab to do some of the same stuff

---

### Post by logos34 on 2007-12-25
> **zchenyu said:**
> Thanks for all your help Logos, my friend figured it out. The problem was that the info in /boot/grub/menu.lst was inaccurate. I basically changed all the "(hd0,5)" to "(hd0,4)"

Huh? You shouldn't have had to change it back because it should never have changed in the first place.  All you did is resize it--the partition is inside an extended.  Unless you were mistaken in your first post:
> 
hda 4 - extended

    * hda 5 - ext3 (Ubuntu)
    * hda 6 - linux-swap (swap space for hda5)
    * hda 7 - linux-swap (swap for a previous installation of Ubuntu, didn't remove previously)

---

