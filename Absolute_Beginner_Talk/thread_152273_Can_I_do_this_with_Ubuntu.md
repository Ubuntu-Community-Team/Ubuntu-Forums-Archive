---
title: "Can I do this with Ubuntu?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by shane.reid on 2006-03-29
1) Sync my Treo 650

2) Sync it over Bluetooth

3) Use it for DUN

4) Use a bluetooth mouse

Trying to swtich fulltime... but I;m about 3 years removed from using Linux regularly (used to use Mandrake/Gentoo depending upon the system for years)

And these newer technolgies I have no linux experience with...

---

### Post by nickj6282 on 2006-03-29
I can't answer the first 3 (although I'm curious myself) but to get a bluetooth mouse working is easy. Just push the connect button on the mouse, then do:

```
hcitool --scan
```

That will tell you what devices it finds and their mac addresses (if you don't already know the mouse's mac address). Then to connect do:

```
hidd --connect xx:xx:xx:xx:xx:xx
```

If you want to connect to your mouse every time the computer boots, change the options in the /etc/bluez-utils file. The comments in there show you what to do to connect to the mouse on startup (and I can't remember off the top of my head anyway).

good luck
-Nick

---

### Post by shane.reid on 2006-03-29
Extremely helpful...

I'll post here if I find out about the rest of the questions.. unless someone replies.

You simply MUST be able to get DUN working in some fashion... perhaps not easy, but if it is possible... I'll find out how from someone somewhere..

---

### Post by warpforge on 2006-04-08
For DUN, check out my new wiki entry:
[https://wiki.ubuntu.com/BluetoothDialup](https://wiki.ubuntu.com/BluetoothDialup)

---

