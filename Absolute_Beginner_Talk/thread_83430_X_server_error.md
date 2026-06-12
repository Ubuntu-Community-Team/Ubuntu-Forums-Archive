---
title: "X server error"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by halfshadow on 2005-10-28
i just did the install and it is saying there is an error with my xserver and it cant load the gui...any clue?

ive got an athlon64 2800+ so I installed the amd64 bit cd

---

### Post by Ampersand on 2005-10-28
log in at the command-line iterface you're given, then try running 
```
sudo dpkg-reconfigure xserver-xorg
```
If this doesn't work, try
```
cat /var/log/Xorg.0.log
```
scroll down using the arrow keys until you find the lines starting with (EE), and this will tell you what the problem was. If it doesn't mean much to you, post it here, and someone will probably be able to tell you how to fix it.

---

### Post by halfshadow on 2005-10-28
it is saying the error is it cannot find any screens...ive got an integrated 6100 on my motherboard and ive got the motherboard driver cd in my cdrom...how do i get the drivers onto ubuntu or to work there?

---

