---
title: "Linux.Lion worm found by ClamAv on windows partition"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by laughingstock on 2006-02-23
Anybody run into this?  Trying out Ubuntu on my desktop.  Have a relatively fresh (< 1 week) Breezy install.  I also run WindowsXP on the same box.  I ran clamscan  and got the following message:

//media/windows/pagefile.sys: Linux.Lion worm FOUND

So this is on the windows partition, which is read only.  I have read a bunch on this worm, but haven't found a procedure to determine whether it's actually active on my system.  (Everything I read is from 2001...).  So is this an actual infection, or just a file I got while running windows that can't actually do anything, or..?

---

### Post by kaamos on 2006-02-23
could be a false positive as well.. What is a virus scan in windows saying?

---

### Post by stalefries on 2006-02-23
Try doing a scan in Windows. See what it tells you.

---

### Post by laughingstock on 2006-02-23
Good idea.  A full McAfee scan in Windows came up clean.  (Searching in Windows, I can't even find a file named pagefile.sys...)  Doesn't totally set my mind at ease... I'll keep searching the Web to to see if I can find a condition/activity that , if present of my machine, would confirm the presence of the worm.

---

### Post by nalmeth on 2006-02-23
I don't think windows can write to your ext3 ubuntu partition, but it's weird that McAfee wouldn't pick this up. Are your virus definitions up to date? Do you have another antivirus app you can try? I think there are some free ones for windows

---

### Post by LordBug on 2006-02-23
Pagefile.sys is the Windows swap file.  Windows will hide it by default.

ClamAV hitting Linux.Lion in it is very probably a false positive.

---

### Post by mwanafunzi on 2006-02-23
check this link out...if you already have not read it. Like all the stuff that I have found dates back to 2001..

[http://www.f-secure.com/v-descs/lion.shtml]("http://www.f-secure.com/v-descs/lion.shtml")

---

### Post by newuser111 on 2006-02-23
its a false positive the lion worm infected Berkeley Internet Name Domain (BIND) servers running on linux in 2001 but has long been patched, besides why would it be in the windows swapfile?

---

