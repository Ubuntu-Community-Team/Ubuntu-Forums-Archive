---
title: "Kernel Compilation For People Who Have No Internet Connection"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Kiddalee on 2006-07-03
Or rather, people who have to go through someone else's computer to download things.

Everything I must do appears to rely on apt-get, [including kernel compilation]("http://ubuntuforums.org/showthread.php?t=56835&highlight=%2Fusr%2Fsrc%2Flinux").  Even Synaptics tries to download a kernel when I ask it to install the one that should already be on my Ubuntu CD.

Is there some way to change Synaptic's settings to look on the CD instead of online?  Or some way to access my CD ROM drive from the terminal?  Anything that will help me compile my kernal source directory?

Making my modem work should not have to rely on apt-get.

---

### Post by Qrk on 2006-07-04
You can make Synaptic look for your cd rather painlessly

```
sudo gedit /etc/apt/sources.list
```

There should already be a line in your sources.list corresponding to the CD, you should only need to uncomment it.

---

