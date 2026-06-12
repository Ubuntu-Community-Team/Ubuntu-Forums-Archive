---
title: "Hard Drives and  Filesystems"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by censored77 on 2007-04-24
When I installed Ubuntu I didn't know anything about Linux filesystems, so I did what seemed logical at the time. I have two HDDs, the first was the Windows system drive, the second I was using as a media drive with Gbs of mp3 and video files. The second drive also had about 60Gb which had never been partitioned, which I set-up as follows:

HD1: Windows partition, Ubuntu root partition
HD2: NTFS Media area already full of stuff, Ubuntu swap area, new ext3 drive

I then mounted Windows drive as sda1, Media Drive as sda2, which are both fine and accessible. i can also write ok with the NTFS package.

However, since I didn't know these things, the ext3 drive which I mounted *** sdb3 isn't accessible as I don't have permission. Is there a simple way that I could change this to my /home area or at least to an accessible place for files?

---

### Post by Happy_Man on 2007-04-24
Use the code:

```
sudo chown -R username /mount_location/
```

---

### Post by censored77 on 2007-04-24
will that replace my existing home folder, or give me a second?

---

### Post by Happy_Man on 2007-04-24
Neither, it will just transfer ownership to you from root. Simply substitute "username" with your username, and "mount location" with the location of the hard drive in /media. For example, if your drive was mounted with the name "Windows," the code would be:

> sudo chown -R censored /media/Windows

---

### Post by censored77 on 2007-04-24
Sorry, stupid question! I looked up the command and I understand now... thanks for your help...

---

