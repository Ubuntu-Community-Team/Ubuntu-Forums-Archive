---
title: "visual interfase"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Michael Reyes on 2007-10-30
Hello, 

i'm new in linux and i just installed the ubuntu server 7.0 in one machine, but is only in console mode, there is any way to switch to visual mode in ubuntu server????

thanks in advance for your help.

---

### Post by taurus on 2007-10-30
Visual mode you mean desktop--window?  You need to install it before you can use it since the server version is only a command line.

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

