---
title: "read only hard drive"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by estin on 2008-01-06
i've been using ubuntu for while now but since i need windows once in a while i went back to a dual boot on my desktop. i have a 80gb split in two with the two os's and 250gb slave drive for just storage.  my problem is in ubuntu the 250gb drive is read only.  i tried it in NTFS and EXT3 and it won't allow me to write to it.  i formatted a small partition in FAT32 and it let me write files to but thats it.  i even logged in as root and tried to enable permissions for creating and deleting files on it but it said "drive is read only"  so i'm kinda stuck.  any advice is appreciated.

---

### Post by spydon on 2008-01-06
Do you run Gutsy Gibbon (7.10)?

---

### Post by estin on 2008-01-06
its the 7.04  i beleive thats edgy eft or something.

---

### Post by peitschie on 2008-01-06
If you're running 7.04, you need to use NTFS-3G to get write-access to the NTFS drive.  See this link: [http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty).  You may need to configure your fstab to manually use the ntfs-3g driver... I'm not sure how well this stuff auto-configures unfortunately.  Post if you aren't sure how to do this and we can walk you through it though :)

---

### Post by estin on 2008-01-06
i guess it was feisty, not edgy.  lol  anyhow, i'm upgrading right now to 7.10 gutsy.  i did also try the ntfs-3g but it didn't work.  the thing i don't get is it won't let me write to a ext3 formatted drive either.

---

### Post by peitschie on 2008-01-06
That sounds suspiciously like a permissions problem to me.  Could mean you're mounting it so that only root can read and write (so for example, 'sudo touch testfile' would work, but 'touch testfile' would not)

If the problem still persists under Gutsy, let us know... the first thing we will want is for you to post your /etc/fstab file so we can see how you are mounting the drive :)

---

### Post by estin on 2008-01-06
yeah i wasn't able to write to it while logged in as root either.  it just said the drive was read only.  i tried to log in as root to grant write permission but i couldn't write to it as root either.  lol

---

### Post by teryowen on 2008-01-06
show output of:

sudo mount

---

### Post by estin on 2008-01-06
upgrade to gusty fixed it.  don't know what the problem was but doesn't matter now i guess. its annoying though i spent all day trying to fix something a simple version upgrade would have fixed.

---

