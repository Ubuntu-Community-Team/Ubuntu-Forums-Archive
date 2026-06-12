---
title: "video mode at boot"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by erciesielski on 2006-07-25
When I boot my system my monitor won't work. It says "VGA Mode Not Supported." How do I fix this?

---

### Post by encompass on 2006-07-25
Sounds like your moniter is older.  What kind do you have?

Boot into recovery mode by pressing excape during the count down at the start of the computer... then select recovery mode and press enter.

log in if needed and type...
sudo dpkg-reconfigure xserver-xorg
press enter if it is a setting you don't need to change.  But when it comes to the resolutions that your monitor supports... besure to "X" the resolutions that your monitor can handle.

Sounds odd that your screen can't take 1024x768

---

### Post by erciesielski on 2006-07-25
It's a MAG Innovision. I've never heard of it. My girlfriend got it from her aunt's office. It handles it on windows xp, but not my linux machine. I don't know why.

---

### Post by erciesielski on 2006-07-25
It seems to have worked. I had to change some settings with my video card. Thanks for your help.

---

### Post by encompass on 2006-07-25
great... if you can figure out what it was, it would help people here if the problem happens for another.  So PLEASE enter the answer if you know it.

---

### Post by The_Shady_1 on 2006-07-25
I had just about the same problem with my MAG monitor when I was changing over from a CRT monitor. However this was back in Breezy.

---

