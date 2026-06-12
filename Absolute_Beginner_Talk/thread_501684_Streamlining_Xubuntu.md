---
title: "Streamlining Xubuntu"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by zingyrob on 2007-07-15
Hi all,

Xubuntu taking up over 5gb space on a clean install?
Is this normal, and how do I get it down if all I use is Office and Web?

---

### Post by gn2 on 2007-07-15
My Xubuntu installation has less than 3gb of used space on my / partition, I installed from the "Alternate Cd" and have added more software since, I have a separate /home partition as well.

---

### Post by crimesaucer on 2007-07-15
That's doesn't sound correct zingyrob.

This was good guide for dual boots with xp using the Alternate CD (and a FAT32 file to transfer files): [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

---

### Post by zingyrob on 2007-07-15
Well when I go into the file manager and check the properties on the 'file system' it says 5.1gb.Would it be possible that there are installation files somewhere? Or does it not work like that in Linux?

---

### Post by crimesaucer on 2007-07-15
xubuntu should be around this size: [https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/disk-space-needed.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/disk-space-needed.html)



Did you create a Fat32 file or anything?


....also if I check the properties of my File System, it includes my /media/hda1 with my dual boot windows, so even though I only have 9GB used out of a possible 15GB of Linux, it shows as 40+GB size.

---

### Post by zingyrob on 2007-07-15
I had XP, rebooted using the LiveCD, clicked on install. Let the installer merge 2 partitions and  take off xp.

---

### Post by crimesaucer on 2007-07-15
I didn't install that way, so I can't help you with that...I'm also new to Linux (10 months), so I can only help with issues that I've gone through.

---

### Post by crimesaucer on 2007-07-15
Maybe try to run this in Terminal:

```
sudo apt-get autoclean
```

---

