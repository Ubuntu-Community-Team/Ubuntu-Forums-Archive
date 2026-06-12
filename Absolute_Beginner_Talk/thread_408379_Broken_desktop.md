---
title: "Broken desktop"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Lars Skovbo on 2007-04-13
My desktop is not responding when i right click on it, and my icons/launchers are gone. Its not the whole interface that is broken. The menu bars and all programs still work. But the background is gone :( It happened when i wanted to install document templates, so i could create a open office document from the RMB menu. I created a folder called Templates and unpacked a tarball worth of stuff to get the menu right. This works but at  a price it seems ^^ (i followed a guide on the forum). The problem occurred because the shortcuts (in the RMB menu) didn't show. So i decided to restart the x-server - closing it with ctrl-alt-F4. I tried to 'startx'. The prompt told me to remove a file called /tmp/.X0-lock, so i did. I have done this before with no problems. But on starx the desktop didn't appear so i restarted the whole system, thats when the desktop failed to load. What should i do?

---

### Post by aberry5555 on 2007-04-13
try 

```
sudo dpkg-reconfigure xorg.conf -phigh
```

this will reset your Xserver configuration file.

or, if that fails to work

```
sudo dpkg-reconfigure xorg.conf
```

(this time without the "-phigh")

This will as you to start from the absolute beginning, hehe.

---

### Post by eentonig on 2007-04-13
Ah, someone beat me to it. Thanks aberry5555'

---

