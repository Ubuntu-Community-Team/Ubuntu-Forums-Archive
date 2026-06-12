---
title: "ubuntu server"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by rbinlex on 2007-11-17
I'm new to linux but have been using ubuntu for a while and have fallen in love.  I am now trying to use ubuntu server 7.1 on a new machine as a test base.  I installed it as a file server.  When I boot I only get the command line.  I was hoping for a GUI on the server like is on the normal ubuntu.  I tried some things I found in "Linux Cookbook" but none of them worked.  Is the GUI possible and what am I missing here?

Thx for your patience.

---

### Post by taurus on 2007-11-17
Server is only a commandline so if you want gnome window manager, you need to install it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

