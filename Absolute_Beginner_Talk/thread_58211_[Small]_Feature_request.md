---
title: "[Small] Feature request"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by mozz on 2005-08-19
Please, please, please, please make Ubuntu update LILO automatically after a kernel update...just felt like my heart stopped when the machine didn't boot  :-# 

I mean, I know how to fix it (NOW) but other beginners don't...and it's not that of a great fun digging in old debian-forums for solutions for problems, which shouldn't exist in an user-friendly distribution ;)

btw: For all those who have Err-messages like:

> Error -3 while decompressing 
> runaway loop modprobe 

etc. after a kernel update using LILO:

Boot into some rescue system (ubuntu live cd), switch to a terminal (STRG+ALT+F1)
Do 'sudo fdisk -l', search for your root partition (/dev/hd*1 probably...)
sudo mkdir /mnt/rescue
sudo mount /dev/hd*1 /mnt/rescue [replace hd*1 with your root partition]
sudo chroot /mnt/rescue
sudo lilo

Now you should get an output like: Added entry: Linux-***..whatever, hth anyone

---

