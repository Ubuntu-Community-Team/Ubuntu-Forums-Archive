---
title: "Unable to get into ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by catchjaga on 2007-04-14
I have installed ubuntu in my system.I have a strange problem..This is what happens,

-->Ubuntu boots
-->I am getting nvidia splashscreen as i have installed nvidia driver
-->When i get login screen it immediately gets crashed shows zigzag colours.
-->i tried going into text mode by ctrl+alt+F2,but didnt work
-->this does not happen whenever i get into recovery mode.In recovery mode i am able to get into x session.
-->Also i am not able to create new users in recovery mode

Please help me.The following is my system config..

AMD64 3200+ (AM2)
ASUS M2N-PV
1 gb ram 

256 mb shared for video

But i am getting memory in nvidia settings as 512 MB


PS.I have installed nvidia driver thinking the problem was because of video driver.

---

### Post by aquavitae on 2007-04-14
Can you post your logs.  They'll probably be under /var/log/messages depending what logging daemon you're using.  You should be able to access it in recovery mode, then just scroll back to where the last boot failed and post the lines leading up to the crash.

---

