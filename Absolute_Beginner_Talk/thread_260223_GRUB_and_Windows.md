---
title: "GRUB and Windows"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by woodpidgeon on 2006-09-18
I have 2 HDs 1 with Windows XP only and 1 with 5 partitions of which one contains Ubuntu.  All has been working perfectly until I decided to mount Windows in an attempt to access my considerable collection of MP3s which are on one of the partitions on HD 2.  Now the GRUB menu on boot up no longer has Windows XP as an option and when I run fdisk -l it lists everything as normal.  I still cant access my MP3s or Windows XP. I hane tried to umount the /media/windows file I created but I get the message windows is not mounted. Can someone tell me what I have done wrong please?

---

### Post by bulldog on 2006-09-18
Windows should be automounted by default and all of your partitions too and visible in /media.

Don't know where it's been wrong but GRUB shouldn't be a part of it,/etc/fstab is the file where you van find all mounted volumes.

To put windows back in your GRUB,

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1
 
You only have to change the hda entry with yours

---

### Post by roberto22085 on 2006-09-18
How exactly did you try to mount your Windows XP partition? All you would have had to do is add a line to the /etc/fstab file telling Linux what kind of partition you wanted to mount. Then you would have to make the directory where you wanted to mount the partition. It should not have changed GRUB at all!

---

### Post by buffy^ on 2006-09-18
ok then from memory, try loading into ubuntu,

then open shell and  sudo root, press enter and enter password

cd /

cd /etc/ 

in here I believe there should be a file call FSTAB, you can edit that and mount the partition.

Yes, I have only used linux for 2 days now so its problably not that accurate, but i am sure some on will be along in a min to clear that up.

---

### Post by bulldog on 2006-09-18
If your partitions are not mounted you can try

sudo mkdir /mnt/windows

sudo mount -t ntfs /dev/??? /mnt/windows

??? stands for the partition you will mount [fdisk -l]

So you can reach your stuff.

If you want to alter fstab or anything else for that matter,be sure to make a backup first!!

---

### Post by woodpidgeon on 2006-09-18
Thanks guys. In the /boot/grub/menu.lst file the windows code appears to have disappeared so I will put that back first and then follow your suggestions. Should I have any further probs I will return.  Thanks for the advice.

---

