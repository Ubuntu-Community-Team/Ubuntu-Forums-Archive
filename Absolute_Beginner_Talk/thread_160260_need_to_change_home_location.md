---
title: "need to change /home location"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by binks on 2006-04-14
i need to move my /home from / to a new location that will take up my entire hdb is this posible and how if so cheers binks

---

### Post by fng on 2006-04-14
This is how i did it : 
- I formatted hdb and made 1 big partition on it.
- mounted the drive as /mnt/hdb
- I created a dir called home on my newly formatted drive : mkdir /mnt/hdb/home
- copied all my files from /home/user -> /mnt/hdb/home/
- deleted the subdir user in /home
- made a symlink user the my new home directory in /home : sudo ln -s /mnt/hdb/home user
- add the drive to automount at bootup, so you'r home is available when you login.

---

### Post by aysiu on 2006-04-14
Another way to approach it...

Format /dev/hdb1 as Ext3 using something like GParted (can be installed through Synaptic).

Mount it ```
sudo mkdir /tmp/hdb1
sudo mount -t ext3 /dev/hdb1 /tmp/hdb1
sudo cp -R /home /tmp/hdb1
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Add a line in there for /home: ```
/dev/hdb1 /home ext3 defaults 0 0
``` Save (control-x), confirm (y), and exit (Enter). Reboot...

---

