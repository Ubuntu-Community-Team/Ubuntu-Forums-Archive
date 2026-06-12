---
title: "[SOLVED] remove programs?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-01-08
I have installed Ubuntu and love it. I decided to try and see if I liked kubuntu and xubuntu. There the problem begins. I didn't really like them so I deleted them using the command: ```
sudo apt-get purge xubuntu-desktop kubuntu-dekstop
```
It deleted them just fine, but it DID NOT delete any of the programs that installed when I installed (k, x)ubuntu. Is there a way to just have it delete all of the programs that were installed? Or do I need to go in and find every little programs?

---

### Post by forestpixie on 2008-01-08
you might be able to get to it by looking at the psychocat pages - getting back to pure gnome, 

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Steveway on 2008-01-08
sudo apt-get autoremove 
that should remove those apps that came along those, now deinstalled, meta-packages.

---

### Post by audwan on 2008-01-08
You might find what programs where installed by looking through the file /var/log/dpkg.log also. Search for xubuntu-desktop and kubuntu-dekstop.

There are some other related posts to be found in the forums also:
[http://ubuntuforums.org/showthread.php?t=566924](http://ubuntuforums.org/showthread.php?t=566924)
[http://ubuntuforums.org/showthread.php?t=197391](http://ubuntuforums.org/showthread.php?t=197391)

---

