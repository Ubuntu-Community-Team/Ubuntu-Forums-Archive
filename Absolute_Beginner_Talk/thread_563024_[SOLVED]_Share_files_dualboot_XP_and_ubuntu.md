---
title: "[SOLVED] Share files dualboot XP and ubuntu"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by juantastico on 2007-09-29
Hi my question is i have a laptop with both ubuntu and xp (dualboot) i will like to send files when i am in ubunto to xp, and viseversa. When i am in ubuntu i can see the windows file but when i drag a file i get the message "you do not have permissions to write to this folder."
On the other hand  when i am on Xp i cant see the ubuntu partition.

Can someone please help me to link a bridge between this two programs?

thanks

---

### Post by Happy_Man on 2007-09-29
Well, for XP, there are very reliable ext3 drivers available. Get them at [http://fs-driver.org](http://fs-driver.org) .  For your Ubuntu to Windows issue, can you please post the contents of the file /etc/fstab here?

---

### Post by rsambuca on 2007-09-29
For complete cross-OS compatibility, I use the previously mentioned fs-drivers for Windows, and then the ntfs-3g drivers for linux to read/write to Windows drives.  To install them on ubuntu, just open a terminal and enter```
sudo apt-get install ntfs-3g ntfs-config
```
Then just open ntfs-config from the Applications-System Tools menu and it will set everything up for you.

---

### Post by ev5unleash1 on 2007-09-29
I think in Gusty you will have the ablilty to read and write the NTFS Drive without any special command.

---

### Post by juantastico on 2007-09-29
Thanks guys i find a very quick solution by downloading ntfs-config 0.5.5. this gave me the write to read and write the windows file. Then a created a new file under the windows partition called Quikshare. Now i can share files among the two systems like a dream. 

I am starting to luv ubuntu 

Cheers :guitar:

---

### Post by quinnten83 on 2007-09-29
> **juantastico said:**
> Thanks guys i find a very quick solution by downloading ntfs-config 0.5.5. this gave me the write to read and write the windows file. Then a created a new file under the windows partition called Quikshare. Now i can share files among the two systems like a dream. 

I am starting to luv ubuntu 

Cheers :guitar:

That is because ubuntu Rocks, and don't let anybody tell you otherwise.

---

