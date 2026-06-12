---
title: "Desktop files in terminal don't match files on GUI desktop."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Protopath on 2006-11-05
I installed another hard drive tonight.  In the process of trying to figure out how to gain access to it I have misdirected my filesystem somehow.

While trying to use disks-admin I set the access path of my new hard drive to the desktop.  That was the wrong method and I followed a tutorial and created a mountpoint named /20gig.  That worked and I have access to the drive.

However, the files I see on my Desktop are not that which is listed while in the terminal.  In the terminal the files under /home/myusername/Desktop/ are those on /20gig (The new hard drive).

I hope this makes some sense.

Thanks.

---

### Post by CatKiller on 2006-11-05
If you've got a partition mounted to the desktop, you should be able to use ```
sudo umount /home/*username*/Desktop
``` to unmount it again.

---

### Post by Protopath on 2006-11-05
Excellent.  Thank you very much.

---

