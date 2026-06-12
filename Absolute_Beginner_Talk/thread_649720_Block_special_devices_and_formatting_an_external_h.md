---
title: "Block special devices and formatting an external hard drive"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Frostmourne on 2007-12-25
Hi, I recently got an Seagate FreeAgent external hard drive exclusively for backups and I wanted to format it as ext3 because I will only access it from Linux. However, when I run  

mkfs.ext3 /media/FreeAgent\ Drive/

in the terminal I get a message about it not being a block special device and if I want to proceed. Wikipedia tells me block special devices are things like hard drives that write in blocks....so why isn't my hard drive being seen as block special?

I don't want to be formatting incorrectly, so thank you for any help.

---

### Post by taurus on 2007-12-25
First, you don't format the mountpoint.  You format the device, something like /dev/sda1 or whatever it is.

Second, you need to unmount it first before you format it.

What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```

---

