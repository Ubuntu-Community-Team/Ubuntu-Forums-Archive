---
title: "moving video files"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by jules2255 on 2007-07-08
when i try to drag files onto another hard drive I have installed it tells me I don't have permission. what do I do? please help

---

### Post by jules2255 on 2007-07-08
I cant copy my files to my back up Hard drive. It tells me I don't have permission. what do I do?

---

### Post by aysiu on 2007-07-08
Internal? External? NTFS? Ext3? FAT32?

More details please.

---

### Post by jules2255 on 2007-07-08
[SIZE="3"]**how do I move files to another disk? It tells me I don't have permission.**[/SIZE]

---

### Post by boralyl on 2007-07-08
The output of :```
sudo fdisk -l
``` would be helpful.

---

### Post by jules2255 on 2007-07-08
i cant move files to my usb hard drive. It tells me that I don't have permission. WHAT DO I DO?

---

### Post by aysiu on 2007-07-08
Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Then paste the output back here.

And please don't cross-post. One thread per problem is best for all involved.

---

### Post by jules2255 on 2007-07-08
Ubuntu  Wont Let Me Drag A File To My Usb Disk Drive. Its Saids I Don't Have Permission. What Do I Do?

---

### Post by aysiu on 2007-07-08
> **jules2255 said:**
> Ubuntu  Wont Let Me Drag A File To My Usb Disk Drive. Its Saids I Don't Have Permission. What Do I Do?
What do you do?

Read posts #2, 3, and 4 of this thread and stop creating new threads on the same topic.

---

### Post by RRS on 2007-07-08
Use the command:

sudo chown <user name> <path to usb disk>

This will make you the owner of the disk.

---

### Post by aysiu on 2007-07-08
> **RRS said:**
> Use the command:

sudo chown <user name> <path to usb disk>

This will make you the owner of the disk.
That won't work for FAT32 or NTFS.

We need more information from the OP about what the exact situation is with the backup drive.

---

### Post by RRS on 2007-07-08
> That won't work for FAT32 or NTFS.
Oops, thanks for the reminder, guess it's been a while since I dual booted.

Yes, jules2255, please provide the results from Aysiu's second post so someone can help you.

---

