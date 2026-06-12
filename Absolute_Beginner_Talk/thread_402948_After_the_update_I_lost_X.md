---
title: "After the update I lost X"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by citaworvk on 2007-04-06
After i received the kernel update to the 386 version, the gui no longer works. I don't know what to do next. 

I tried this :
sudo aptitude install nvidia-glx

but the drivers were already installed

I tried this :
sudo nano /etc/x11/xorg.conf

the file seemed empty

So now I just rebooted from the generic kernel and everything works but I want to make the 386 version work could someone explain what I should do.

This is a great OS I've been using it for a few months I just don't know very much. Thanks in advance.

---

### Post by taurus on 2007-04-06
It's X11, not x11.

```
sudo nano /etc/X11/xorg.conf
```
Otherwise, you can reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

