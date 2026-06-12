---
title: "Automatically mount NTFS RAID on Reboot"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-09-26
I worked out how to manually mount NTFS RAID using this command:
sudo mount -t ntfs -o users,owner,ro,umask=00 /dev/mapper/pdc_jjecchfi /mnt/raid

How do I make this mount automatic on system reboot please?

---

### Post by Cruz on 2006-09-26
Add it to /etc/fstab (see man fstab before).

---

