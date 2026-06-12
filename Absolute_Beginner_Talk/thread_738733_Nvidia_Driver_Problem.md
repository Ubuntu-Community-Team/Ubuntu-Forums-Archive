---
title: "Nvidia Driver Problem"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by poscomp on 2008-03-28
I have version 7.10 on my computer. Went in and allowed restricted driver for Nvidia to load. Did a system reboot and it starts to load then says on the monitor....OUT OF FREQUENCE. System refuses to go further and I am at a loss. Can't load OS...please HELP!!!

Lew Blackman

---

### Post by The Titan on 2008-03-28
you have to lower the refresh rate

---

### Post by poscomp on 2008-03-28
how do i do that?

---

### Post by K-Soul on 2008-03-28
Boot into recovery via grub and post the following in the command line:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Cheers

---

### Post by poscomp on 2008-03-28
Thanks K-soul the fix worked great. Can you tell me what I did?

---

### Post by SOULRiDER on 2008-03-28
You asked dpkg (package manager) to reconfigure xserver-xorg (xorg is in a way the program that gives you a desktop). sudo means you ran the command as a super user and -phigh are options you gave dpkg (just some extra info to make the process shorter).

---

### Post by poscomp on 2008-03-28
**[SIZE="7"]Thanks All[/SIZE]**

---

