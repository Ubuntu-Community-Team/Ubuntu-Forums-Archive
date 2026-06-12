---
title: "Can't Load Other OS in GRUB"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-26
Hey all,

When I restart my computer and try to load one of my other OS in the grub list my keyboard wont work. Its weird, it just started doing this. Does anyone have any suggestions?


Also, how do I see what ports are being used by my computer? I would like to check and see what ports are open and for what.

---

### Post by A4006 on 2008-01-26
If you have a USB or wireless keyboard that uses USB you might have issues with it working before the computer fully boots.  To see what ports are open just look on the back of your computer.  You might have to use a PS/2 keyboard.

---

### Post by spiderbatdad on 2008-01-26
```
man netstat
```

you might want to check out nmapFE in synaptic...running the scan on 127.0.0.1 is loopback...just click the scan button and wait...it doesn't indicate that its doing anything until its done...30 secs or so.

oh after you install it, look in system tools or internet

---

### Post by spiderbatdad on 2008-01-26
also...System>>Administration>>Network Tools

choose port scan tab and enter 127.0.0.1 as the address, then hit scan button.

---

