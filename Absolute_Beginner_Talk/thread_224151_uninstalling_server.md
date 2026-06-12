---
title: "uninstalling server"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by TPhillips on 2006-07-27
Hi all, I am a complete novice with Linux so bear with me.
I thought I had downloaded the disktop iso but it looks like 
I downloaded the sever instead I installed it on my hard drive
with a dual boot for winxp.What can I do to uninstall it and
download the desk top and install it. Thanks Tom

---

### Post by T700 on 2006-07-27
No worries; this happens in the best of families.

Boot to the Ubuntu server installation.  You'll be sitting at a black and white screen that looks rather like the Windows command line.  Type the following, one set of commands at a time, followed by pressing the Enter key.

```
sudo aptitude update
```

Enter

```
sudo aptitude install ubuntu-desktop
```

Enter

Note:  This may take a while--that's normal.

When it's done, restart your computer and you should have the basic desktop installation.  Any problems, just post back and someone will help you.

Welcome to the forum!

Paul

---

