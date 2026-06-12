---
title: "Login Restarts Ubuntu"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Toribor on 2008-01-26
When I login to Ubuntu (I just installed via the alternate CD to an external hard drive) it tells me my session lasted less than 10 seconds and restarts. I am running a Dell XPS M1210 with a dual core 2.4ghz processor, 2gb RAM, and using an external 500gb hard drive connected through USB.

Any advice on this problem. (The failsafe modes wont work either, only whichever user lets me input text...)

---

### Post by taurus on 2008-01-26
What filesystem did you format your external harddrive when you installed Ubuntu on it?  Can you log in with your username and password after you press <Ctrl><Alt>F2?

---

### Post by Toribor on 2008-01-27
The hard drive is formatted in NTFS, I'll see where I can get with ctrl-alt-f2, and go from there.

---

### Post by taurus on 2008-01-27
You installed Ubuntu on a ntfs filesystem!  

Good luck with it because you will need it.

---

### Post by Toribor on 2008-01-27
Well, note this is a beginners forum... I have no idea what I am doing. I work primarily with Windows XP and am a pretty PC savvy guy but I know nothing of Linux. I am trying to learn. What file system should I format it in? No where in the install did it ask me to chose, the guided partitioning seemed to be fine for me.

---

### Post by philinux on 2008-01-27
ext3 is probably best it should be an option on the install

---

### Post by Toribor on 2008-01-27
Alright, I tried reinstalling and using the guided partitioner and it worked, which is great. But now Windows can't see my external hard drive. I am missing 500gb of storage which is kind of important... What happened now?

---

### Post by taurus on 2008-01-27
You now need to install fs-driver in windows so windows can read and write to ext3 filesystem.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

