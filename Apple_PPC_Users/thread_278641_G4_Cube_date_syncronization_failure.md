---
title: "G4 Cube date syncronization failure"
date: 2006-10-16
forum: Apple PPC Users
---

### Post by tassoman on 2006-10-16
Hello to all.

There's a problem with my mac G4 cube running 2.15-23-powerpc kernel: automatic date syncronization doesn't work,

when I use sudo it give me back some error with timestamps in the future.

:-k 

Moreover i need date correctly set because I do many crontab tasks

---

### Post by shadie on 2006-10-18
Try the date command, "date 120010182006" that's 12pm Oct 18th 2006

---

### Post by tassoman on 2006-10-18
Doing manually by time-admin works fine. But I would automate it by ntp and isn't working. :|

Maybe some module of the kernel is missing?

---

### Post by DonnieP on 2006-10-18
Are you running Ubuntu in a VM?  I found the articles on this website helpful in fixing clock problems on a Mac.  He also addresses a dual-boot installation if you're not running a VM.

[http://www.xs4all.nl/~hajk/](http://www.xs4all.nl/~hajk/)

---

### Post by tassoman on 2006-10-18
Thanks for that link. But it's about the new intel macs. Did you seen i mean the old [Power Mac G4 Cube]("http://www.google.it/images?q=power%20mac%20g4%20cube")?

---

### Post by linear on 2006-10-18
The "timestamp too far in the future" error is discussed [here]("http://www.ubuntuforums.org/showthread.php?t=173505"); perhaps fixing it will fix your synchronization problem.

---

### Post by DonnieP on 2006-10-19
Running any Linux 2.6 in any VM presents clock problems.  That's why it makes a difference if you're running Ubuntu native or VM. See this article for a discussion:

[http://support.microsoft.com/?kbid=918461](http://support.microsoft.com/?kbid=918461)

---

