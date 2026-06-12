---
title: "Slave HDD vanished!"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by jas992 on 2007-01-17
Hi,

After installing Ubuntu and mounting my slave HDD I have found that I am now unable to view said HDD when I am in Windows XP.
How do I make my slave HDD available under Windows XP as well as Ubuntu?
Any information would be greatly appreciated.

Thanks,
jas992

---

### Post by anaconda on 2007-01-17
What filesystem do you have in your slave HDD?
if you formatted it to ext3 then windows cant "see" it unless you install the fs-driver.

Cand figure any other reason for windows not seeing it. The fact that you mounted it in linux wont affect windows seeing it.

---

### Post by jas992 on 2007-01-17
I didnt change the filesystem. It is either NTFS or Fat32.

---

### Post by pebo on 2007-01-17
Can you post the output of ```
cat /etc/fstab
```from your ubuntu installation?

---

