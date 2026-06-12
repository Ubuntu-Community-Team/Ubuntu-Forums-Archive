---
title: "Changing name for partition and another ??"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by sirisaac87 on 2008-04-05
I just moved my home drive to a different partition, but when I click on that partition i have to click on my user name to access the home folder is it possible to have it so I click on the partition/drive and the home drive just automatically open?

Also how do I change the name of this partion? its name sda3 right now

---

### Post by tamoneya on 2008-04-05
i think what you need to do is add /dev/sda3 to your fstab file so that it is automatically mounted at boot.  This would mean that you dont even have to click on it.
```
sudo nano /etc/fstab
```
add this line
```
/dev/sda3        /home     ex3t    defaults     0   0 
```
that is assuming it is an ext3 filesystem which is the default

EDIT: typos

---

### Post by sirisaac87 on 2008-04-05
ok how do I change the name of this partition?

---

### Post by Walc on 2008-04-05
right click - rename ? :P

---

### Post by sirisaac87 on 2008-04-05
I tried and this is the message that came up "Sorry, couldn't rename "66.8 GB Volume: sda3" to "Home Drive"."

---

### Post by conscious on 2008-04-05
Try this:
```
sudo e2label /dev/sda3 Home\ Drive
```

---

### Post by sirisaac87 on 2008-04-05
Where do I put the name I want the drive or partition to have??

---

### Post by conscious on 2008-04-08
After the command (e2label) and device name.

---

