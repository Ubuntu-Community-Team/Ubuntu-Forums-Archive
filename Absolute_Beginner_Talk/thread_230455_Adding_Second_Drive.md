---
title: "Adding Second Drive"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by djmoffat on 2006-08-06
I've got Ubuntu installed and running! Now, I want to access my second hard drive. I can see it in the "computer browser", but if I double click on it, it says "[COLOR="Red"]Unable to mount the selected volume[/COLOR]'. In the more details portion of the window I see these errors...

[COLOR="Red"]error: device /dev/hdb1 is not removable[/COLOR]
[COLOR="Red"]error: could not execute pmount[/COLOR]

Any help would be great!

---

### Post by orb9220 on 2006-08-06
What is the drive ide? fat32,ntfs,ext3 ?

---

### Post by djmoffat on 2006-08-06
This drive used to be a storage drive on my Windows PC. I believe it is IDE-NTFS.

Dave

---

### Post by confused57 on 2006-08-06
Here's a link for mounting a Windows partition:

[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by orb9220 on 2006-08-06
But you won't be able to write to ntfs without a special linux program called 3g-ntfs or some such.

I suggest reformat to fat32 for access from windows or linux.

Backup or move stuff you don't want to lose.
If you are going to use only for linux then format it to ext3

---

### Post by djmoffat on 2006-08-06
You totally rock! That link did the trick!

Thanks much!
Dave

---

