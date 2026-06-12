---
title: "Need help with GParted / Moving Ubuntu to new HD"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by benmarvin on 2007-08-02
I installed Ubuntu on my dad's computer, it's dual boot with Win XP on the same HD. Now he got a new HD and wants me to put Ubuntu on the new one and leave more room for windows on the first one. I booted with the GParted liveCD to try and delete the partition then resize the Windows one back to the full HD, but it keeps getting hung up on "Mounting media". It lists HDA, hd1, hd2, etc, then stops on "HDB". Am I doing something wrong? Is it the software or maybe my hardware?
Is there an easier or better way to accomplish what I want to do?

---

### Post by nitro_n2o on 2007-08-02
if you delete your ubuntu's partition i believe that you'll loose your installation.. try to resize the partition and move your /home folder to the new drive only that will save some space.. 
you should unmount media before resizing that is 
```
sudo unmout /dev/hda? 
```
? is the number of the drive you want to resize.. or just do this from the GUI

---

### Post by benmarvin on 2007-08-02
Yes, I do want to remove the ubuntu installation. It was preliminary, just a test install. I want to install fresh on the new hard drive. Oh, I forgot to mention, the ubuntu won't even load the gui since there's like no space left on the partition it's installed on.

---

