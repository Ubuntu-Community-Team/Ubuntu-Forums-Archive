---
title: "XSane Help please (device detection)"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by petersjm on 2007-01-01
Hi guys,

**Note: This issue is now resolved.**

Got a new all-in-one printer w/ scanner (HP C3180 - nice!) but I've come across a slight problem. XSane won't detect it unless I run the following code:

```
$ sudo /etc/init.d/hplip restart
```

Then it works fine, just as it should do. Unfortunately, when I log out and in again (or restart, for that matter), I have to run the command again in order for XSane to find the device. Is there some way I can do this automatically on startup, or some way to avoid the need for this? It's a pain having to do so every time I want to use the scanner... Thanks in advance for any help you can offer :D Happy New Year!

{EDIT}
I thought I'd try putting the above code in Sessions > Startup Programs - but that didn't work. It seems it's not an XSane problem, but an HPLIP problem. If anyone can help so that I can "restart" HPLIP every session, that would be much appreciated :)

---

