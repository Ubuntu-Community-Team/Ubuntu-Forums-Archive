---
title: "Backing up files in Photorec"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by The Transporter on 2008-02-14
Recovering Data...  I'm in Photorec, and would like to have it recover the files to my external drive (sdb).  When in the shell, it doesn't seem to recognize the "cd" command to change directories, and can't find the either the internal or external drives when I try to mount them to copy the files or photorec to another drive (if it uses the current drive).

I've read articles with people saying they copied their recovered files to the external drive, but they don't say how. The Linux distro that comes with the recovery cd doesn't seem to have a drag and drop window situation, and Midnight Commander was foreign to me.  

Any ideas?

---

### Post by aysiu on 2008-03-18
I realize you posted this four weeks ago, so I'm not sure if you still need help, but if you do, please post the output of these commands: ```
sudo fdisk -l
df -h
```

---

