---
title: "ubuntu on 2 hd's kernel panic!?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by mr. deeds on 2007-03-27
Hi all,

I bought a new sata drive and installed it. Of course I chose to use Ubuntu on this drive. However, when I boot from the GRUB I can no longer boot Ubuntu on the previoius sata drive. It gets hung up while trying to mount the root file system. I tried using recovery mode and I get a kernel panic no syncing. Can someone generously explain what has gone wrong here and how I might fix it? My original Ubuntu has most of my work and applications that I would like to keep. Any help would be appreciated...

Deeds

---

### Post by martinw89 on 2007-03-28
My guess is that GRUB is instructing the kernel from Disc B to run Disc A, but this is just a guess.  If you post your grub.conf (located in /boot) I might be able to help more.  Basically this error means that your kernel could not mount the root filesystem, which is why I'm guessing that GRUB is telling it to mount the wrong fs.

---

