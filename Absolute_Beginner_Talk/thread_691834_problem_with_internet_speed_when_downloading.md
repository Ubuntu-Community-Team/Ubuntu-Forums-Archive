---
title: "problem with internet speed when downloading"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by Kuko.sk on 2008-02-09
I have a small problem which have to be solved... when i am downloading something for example from rapidshare, and i want to open a webpage, it loads a VERY VERY long time... is there some way to force the firefox to slow down the download, and move faster ? :D THX

---

### Post by NightwishFan on 2008-02-09
You can use the wget command in the terminal. Copy the download link, and type this in the terminal

wget --limit-rate=20k [http://www.webpage.com/filename.ext](http://www.webpage.com/filename.ext)

Change the [http://www.webpage.com/filename.ext](http://www.webpage.com/filename.ext) to whatever it is you are downloading.
You can also change the limit to whatever you want. 

wget --limit-rate=10k webaddress

The file will be downloaded into   /home/yourusername  by default.

---

### Post by zerhacke on 2008-02-15
> **Kuko.sk said:**
> I have a small problem which have to be solved... when i am downloading something for example from rapidshare, and i want to open a webpage, it loads a VERY VERY long time... is there some way to force the firefox to slow down the download, and move faster ? :D THX

Sounds to me like you're having the standard IPv6 problem.  Add ipv6 to the bottom of your /etc/modprobe.d/blacklist file and reboot.  Your pages should pop up very fast afterwards.

Why Ubuntu has IPv6 enabled by default is beyond me.  Nobody uses it yet.

---

