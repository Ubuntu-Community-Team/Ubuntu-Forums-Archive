---
title: "Where Does Synaptic Save Downloads?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-17
I use synaptics package manager to download and install software. I noticed that whenever I reinstall a previously uninstalled software it does not need to redownload. I want to know where are these .deb files that synaptics uses to reinstall.

---

### Post by m!key on 2007-07-17
In /var/apt/cache/ if i remeber correctly (not behind an ubuntu box atm).

---

### Post by bme on 2007-07-17
hmm...
I saw it in /var/cache/apt/archives

Thanks anyway..

---

### Post by Xiobe on 2007-07-17
I've got a desktop and a laptop computer both running Ubuntu. I am wondering if I could download the .deb files only once, lets say on my desktop, and use the /var/cache/apt/archives from my desktop to update my laptop.

---

### Post by forestpixie on 2007-07-17
I think you can..sort of at least. 
You might have a problem with dependencies though.

Found these have a look 

[http://ubuntuforums.org/showthread.php?t=502234](http://ubuntuforums.org/showthread.php?t=502234)

[http://ubuntuforums.org/showthread.php?t=452823](http://ubuntuforums.org/showthread.php?t=452823)

Hope that helps

---

