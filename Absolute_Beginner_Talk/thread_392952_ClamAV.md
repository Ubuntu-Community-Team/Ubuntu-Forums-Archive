---
title: "ClamAV"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Jimmy4eyes on 2007-03-25
I've been reading some of the other posts concerning the very low possibility of catching a virus with Ubuntu. I do have ClamAV installed though, I still have years of windows habits to throw off. One question did occur to me though. 

If I downloaded a file infected with a windows virus, say to transfer over to my XP laptop, would ClamAV detect it, and if yes, could it/would it deal with it for me?

---

### Post by Kobalt on 2007-03-25
ClamAV only scans for infected files, it won't deal with it. And actually that's quite the only thing you need since 99,99% of infected files you'll find will be made for windows infection. So all you need to do I guess is to delete them permanently... 
If you want to learn more about security : [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by Sef on 2007-03-25
> ClamAV only scans for infected files, it won't deal with it.

Not true.  The default is to report is, but you can change that to remove or quarantine the malware.

---

### Post by Kobalt on 2007-03-25
> **Sef said:**
> Not true.  The default is to report is, but you can change that to remove or quarantine the malware.
Woopsy you're right... 
> You can add --remove to the clamscan or clamdscan commandline.
My mistake then :)

---

### Post by euler_fan on 2007-03-25
The advice I have seen is to let ClamAV identify files as good or bad and then google the files you are suspicious of (since there are some large and good databases out there) as well as perhaps posting them to the security forum for further advice. Then, once you have confirmation, delete them permanently.

[This thread]("http://ubuntuforums.org/showthread.php?t=318091&highlight=install+clamav") has instructions to set up nightly scans and alert you to anything it finds in the morning. Might be worth checking out if you are looking for peace of mind.

---

