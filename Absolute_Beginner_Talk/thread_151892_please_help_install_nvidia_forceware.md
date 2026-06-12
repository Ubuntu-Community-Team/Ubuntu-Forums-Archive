---
title: "please help install nvidia forceware"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-03-28
hiyas

How do I point to file in my directory? IE desktop. is it just CD/ Desktop?......I;m trying to install nvidia drivers.

I downloaded the latest Nvidia Forceware driver, to my desktop. Can someone please tell how to install it? or point me to a place that will?

I've done a search, it seems I need to make a path to the desktop in the terminal? don't know how to do it.

Please help if you can. thanks!

Gordo

---

### Post by Stealth on 2006-03-28
Your desktop is in /home/username/Desktop. In which case, if you just open up a terminal and do a:
```
cd Desktop
```

you should be there. Though I wonder why you don't do a simpler:

```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```

To automatically install the drivers, dependencies, and have it activated for you...

---

