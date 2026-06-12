---
title: "How do you use the LiveCD?"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by maaronB on 2006-09-27
I don't really have any problems, I am just curious.  I thought it was possible to use the programs from your harddrive from the CD.  But I can't mount my harddrive from the LiveCD(It is actually the generic Install CD if there is a difference.)
Again everything works and I am just curious, because I have heard that a LiveCD can be used to gain root access, but I can't even see my /home directory.

---

### Post by aysiu on 2006-09-27
Just because you mount your hard drive doesn't mean you can use the programs from the hard drive.

Ubuntu's deficient in that you have to manually mount partitions using the live CD (Knoppix and Mepis can mount them with a single click).

You *can* mount the partitions, though. What's the output of these commands? ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by maaronB on 2006-09-27
I don't know I took the CD out and rebooted through the HardDrive, but you have already answered my question.  Thank You.

---

