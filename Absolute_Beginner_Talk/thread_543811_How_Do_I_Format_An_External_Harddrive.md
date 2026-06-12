---
title: "How Do I Format An External Harddrive?"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ibohren on 2007-09-05
I have an external hard drive that is already formated to NTFS. I want to reformat it to ext3 for use with my Ubuntu laptop. I have read through the forums and searched around online, but I can't seem to find any clear instructions on how to do this using Ubuntu. I tried running fdisk from the terminal but I can't seem to figure out what I need to do from there. Can anyone walk me through this?

Thanks!

---

### Post by anaconda on 2007-09-05
well.. gparted propably is the easiest way.. but I always do formatting from the terminal
```
sudo fdisk -l
sudo mke2fs -j /dev/XXX
```

the fdisk -l is just for recognicing the correct drive. (what to put in the place of XXX.) And the mke2fs -j is the actual formatting command. With the option -j it will be ext3 filesystem.

then you probably should also use 
tune2fs -m 0 /dev/XXX
to change the reserved blocks % for root from 5% to 0%. You will gain 5% more space. with this. (there is no point in reserving 5% of the disk for root if you dont have ubuntu on the external disk. 

and you will have in the place of XXX eg. sda1, sdb1 or something like it.. whichever is the drive you want to format..

Oh.. and when you run the mke2fs or tune2fs commands the drive should be connected, but unmounted..

---

### Post by Mykle87 on 2007-09-05
Install Gparted (in synaptic)
Open Gparted and select the external hard drive from the drop down menu
Delete the ntfs partition and create a ext3 partition
Apply changes

Good luck!

---

