---
title: "Mount"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by benjiej on 2006-02-08
How do you mount your /root and /home from the Live CD? When I pull up /etc/fstab it will see my swap file 
"/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda7 swap swap defaults 0 0"

But as you can tell it doesn't see anything else.

---

### Post by Pragmatist on 2006-02-08
What are the directories in the /dev/mnt directory  Is there anything like /dev/hda1  or whatever your partitions are called?  if there is, try: ```
su
``` and then ```
mount /dev/hda1
``` switch into /dev/mnt/hda1 and your are in the root ( / ) of your hard drive system

---

### Post by benjiej on 2006-02-09
I get "Unknown ID"

---

### Post by Pragmatist on 2006-02-09
You get that when typing "su" or when running "mount" ??  If it is for "su"  tell me what you get by just typing "mount" by itself.

Also, I'm not exactly sure how Ubuntu's LiveCD works.  Knoppix is  the LiveCD I've used and I recommend it.  There, you can do the "su" and then have full privileges on your own system.

---

### Post by aysiu on 2006-02-09
First of all, it's a lot easier to do this with Knoppix, as it's intended to be a live/recovery CD.

If you must, though, I would do ```
sudo fdisk -l
``` to see where your desired partition is. Let's say, for argument's sake, that it's /dev/hda1. If so, do this ```
sudo mkdir /temp_home
sudo mount -t ext3 /dev/hda1 /temp_home
gksudo nautilus
```

---

