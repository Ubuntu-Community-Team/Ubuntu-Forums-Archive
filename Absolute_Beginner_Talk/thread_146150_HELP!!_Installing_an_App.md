---
title: "HELP!! Installing an App"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Anomaly on 2006-03-17
Hi, let me start off by thanking you guys for any responses to this thread. I'm having a problem installing wpa_supplicant.  When I type

make

I get,

bash: make: command not found

am I in the right directory? (the one with the makefile in it?).
The same thing happens when I try to 

sudo make install

Thanks again for the help.

---

### Post by FizDev on 2006-03-17
Strange... it seems like you don't have it.
Try this :
```
sudo apt-get install make
```
and then try again to install wpa_supplicant.

By the way, you could install wpa_supplicant simply by doing :
```
sudo apt-get install wpasupplicant
```

---

### Post by Mustard on 2006-03-17
Actually its because the tools for compiling programs are not installed by default.  The first thing to install when compiling programs is this one...

```
sudo apt-get install build-essential
```

---

