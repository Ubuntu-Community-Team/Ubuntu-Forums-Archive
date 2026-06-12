---
title: "System log suppressing messages?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by wolf3491 on 2008-03-30
I get this message repeated in the system log:
Mar 27 11:09:15 bryan-laptop kernel: [ 759.980000] printk: 2 messages suppressed.
nothing is currently attached, as i thought it was my usb mouse.  What does this mean?

---

### Post by c-ron on 2008-03-30
Hi,
What is the result of: 
```
cat /proc/sys/kernel/printk
```
It should be some numbers...

Also, do you see these when you're disconnected from the internet?
Are you running a custom kernel?

Put the contents of your /var/log/messages file on [http://pastebin.org](http://pastebin.org) and link to it from here.

---

### Post by wolf3491 on 2008-04-02
4    4   1   7

I get it when Im connected or disconnected.  I dont think I'm using a custom kernel.

Here is the message file: [http://www.pastebin.org/26898](http://www.pastebin.org/26898)

---

