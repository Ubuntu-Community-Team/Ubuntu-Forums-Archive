---
title: "Harddrive formatting"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by HenningS on 2007-05-17
Noob question:
I have a 250gb external harddrive. I want to reformat it. Problem is, I can't back it up anywhere. Can I use gparted to create a 125gb partition on it, move all my stuff (about 110gb) on that partition, format the other partition, and then make it one again?

---

### Post by Nekiruhs on 2007-05-17
Yes, you can shrink your old one, make a temporary FAT32 partition, format the old one to ext3 for Ubuntu, move files from the FAT32 to the ext3, delete the FAT32, grow the ext3 to fill the drive. That should do it for you.

---

### Post by HenningS on 2007-05-17
Sounds very good, pretty much what i had in mind. One problem though: When I open the drive in gparted, it says there's 230GiB of unoccupied space. What now?

---

### Post by Nekiruhs on 2007-05-17
Do you have more than one hard drive, if so you might be looking at the other. Check the little drop down box in the top right corner for other drives.

---

### Post by HenningS on 2007-05-17
Nah, that's what I did. It's exactly the drive i mean, but i think gparted doesn't like me :)

---

