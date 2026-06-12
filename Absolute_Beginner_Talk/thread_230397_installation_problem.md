---
title: "installation problem"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by jaynyls on 2006-08-05
Hey all,

I'm trying to install Kubuntu on my SATA II drive.  As it is now, I've got 3 partitions - one NTFS for WinXP, and two unformatted partitions that I made with Windows installer.  

When I get to the installation part where the partitions are supposed to show up, it just pauses there indefinitely.  I tried running QTParted but it reports not seeing any drive. 

Help would be greatly appreciated.

Jason

---

### Post by djmoffat on 2006-08-05
I was having a similar problem, my was pausing at the install stage. I re-downloaded the iso and created a new cd from it. After that it made it through the entire install.

Hope this helps,
Dave

---

### Post by pdub on 2006-08-05
You may want to consider deleting the partitions that you created via Windows and then let Ubuntu create a root and swap partition for you during install.

---

### Post by jaynyls on 2006-08-06
I tried removing the Windows created partitions, merged everything back to a single NTFS Windows partition, then tried installing.  Same result.  Then I tried resizing the Windows partition to leave about 75GB free space.  Same result.

Oddly enough, Suse 10.1 has no problems whatsoever recognizing my hard drive's partition setup, no matter what it is.  I cannot be something with the disc.  What am I doing wrong here?

---

### Post by pdub on 2006-08-06
Try creating the swap and root partitions using Suse 10.1 CD or grab a copy of Knoppix to create the partitions. Then see if Ubuntu can use them for install.

Other than that I don't know what else to advise.

---

