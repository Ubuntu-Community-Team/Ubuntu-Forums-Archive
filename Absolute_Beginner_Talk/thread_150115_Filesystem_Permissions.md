---
title: "Filesystem Permissions"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by CeleronXL on 2006-03-25
I have an external NTFS hard drive that's already been automatically mounted. However, the owner permissions are read and execute, and there are no other perms. Problem is, the owner is set to root, so I can't access it. I tried using chmod +r with sudo to change them, but that doesn't do it. I'm a Linux noob. Any way I can get permissions on my main account to read from the drive? Do I have to remount or something? The drive is in /media.

Would help to also be able to read my main hard drive as well.

---

### Post by aysiu on 2006-03-25
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by CeleronXL on 2006-03-25
Excellent! Worked perfectly for my external drive, but not at all for my Windows partition. Hrmf.

---

### Post by aysiu on 2006-03-25
[QUOTE=CeleronXL]Excellent! Worked perfectly for my external drive, but not at all for my Windows partition. Hrmf.[/QUOTE] Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

