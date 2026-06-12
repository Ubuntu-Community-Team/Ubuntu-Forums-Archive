---
title: "ClamAV"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Mauler5858 on 2008-03-19
Can ClamAV scan mounted NTFS drives without any problem.  And another question how can you mount a drive and NOT have an icon on the desktop for it?

---

### Post by wormser on 2008-03-19
Yes it can scan NTFS drives.  Change the mount directory form /media to /mnt to get rid of the desktop icon.  You will need to create a folder in /mnt to mount it to.  There might be another way to hide the icon, but this will work.

Create mount point
```
sudo mkdir /mnt/mountpoint
```

Open /etc/fstab and change /media/mountpoint to /mnt/mountpoint
```
sudo nano /etc/fstab
```

---

