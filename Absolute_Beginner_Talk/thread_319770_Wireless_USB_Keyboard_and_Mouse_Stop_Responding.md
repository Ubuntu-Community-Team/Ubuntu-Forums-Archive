---
title: "Wireless USB Keyboard and Mouse Stop Responding"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by jengo on 2006-12-16
Hi, im having a small issue

I have a Wireless keyboard and mouse, after bootup the mouse and keyboard work, but stop working like after a few minutes. Anyway to fix this? Thanks.

---

### Post by alan_daniel on 2006-12-16
I think the first thing you need to do would be to find the message in the system logs and post that on here. The way you can do that easily is to restart your computer, wait until the mouse and keyboard stop working, and note the time. Then open up a terminal, and execute:

```
sudo gedit /var/log/messages
```

Then find the corresponding time to what happened, see if anything was logged, and if it was, post that. I may or may not know what to do with that, but I am fairly certain that it would help anyone know what's going on.

---

### Post by jengo on 2006-12-16
thanks, i'll try that and let you know what happens

---

