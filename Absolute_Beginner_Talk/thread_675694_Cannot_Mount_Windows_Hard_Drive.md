---
title: "Cannot Mount Windows Hard Drive"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by TygerTung on 2008-01-22
I just Installed Ubuntu 7.10 On my hard drive which I had dedicated to Ubuntu, and was using Ubuntu 7.04 until the new distribution came out and it automatically upgraded but then the internet etc wouldn't work so I just gave up on it and went back to windows XP for a while. I got the shits with windows when it was printing off open office and Abiword all munted, so I decided to bung Ubuntu back on

I downloaded the new 'Live CD' and the internet seemed to be working so Installed Ubuntu 7.10 and it all was fine except when I went to retrieve the document off the windows hard disk it claims I don't have permission to mount that drive or some rubbish like that. My other partition with no operating system works fine, just this one doesn't.

The file is sitting on the desktop if that would have any effect?

Also ubuntu still seems to have a hernia when I have both my Combo drive and DVD writer both connected, so I have to unplug one. when I installed 6.06 it didn't do this?

Cheers,

Sam

---

### Post by jflarm on 2008-01-23
Can you put here the contents of your /etc/fstab file?

---

### Post by TygerTung on 2008-01-23
I am unsure of what that is. How can I get to this magical file?

---

### Post by roboxking on 2008-01-23
hm, you may have to change the root password in order to mount the partition. But if your root password already then, I have another solution. Open the Terminal (Applications-->Accessories-->Terminal) Then type in ```
gksudo nautilus
```. This opens the folder system with root privileges, so you can bypass any inaccessible items. ***WARNING*** Do not abuse using root, as you can seriously ruin your system with it. Hope this helps

---

### Post by tojge on 2008-01-23
> **TygerTung said:**
> I am unsure of what that is. How can I get to this magical file?Just do ```
less /etc/fstab
```

---

### Post by TygerTung on 2008-01-23
Well you know what? I restarted the computer, went into evil windows and moved the file i wanted to the spare partition, restarted the computer back into Ubuntu, and viola! c: appeared on the desktop!!!!! So it seems to be mounting fine now with no input from me!

Well thats ok then, issue solved.

---

### Post by jflarm on 2008-01-23
Do this on a terminal...you can find it in Accessories-->Terminal

sudo apt-get install ntfs-config

This will install a gui application to mannage the write permisions on the internal and external NTFS partitions.

---

