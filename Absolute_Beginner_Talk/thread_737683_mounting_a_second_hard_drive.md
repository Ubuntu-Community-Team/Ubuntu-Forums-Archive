---
title: "mounting a second hard drive"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-03-27
i have recently replaced Windows 2000 with Fluxbuntu on my Dell Dimension desktop and it's running fine, but am unable to access my secondary hard drive were all my music and pictures are at. the hard drive is NTFS partitions if that makes any difference, any help would be appreciated and plz bear in mind thati 'm still pretty new to Linux. thanx

---

### Post by i-am-me on 2008-03-27
Make sure ntfs-3g is installed (it should be installed by default but just in case):
```
sudo aptitude install ntfs-3g
```
Then, after configuring it after installation (if you installed it), look in either /media or /mnt. If it's not there, try a
```
sudo mount -a
```
and look again.

---

### Post by tranquito on 2008-03-27
NTFS shouldn't make too much of a difference. If you want a more GUI approach. Login as root and go to My computer and see if you can mount it from there.

---

