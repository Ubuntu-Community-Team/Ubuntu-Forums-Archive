---
title: "Install Xubuntu over Ubuntu?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by erikaaboe on 2007-02-18
Hello-
I have an Ubuntu Edgy installation on an old-ish Dell Dimension (PII - 512 MB RAM) and it just to be a bit too much for any kind of snappy performance. Also, some of the applications (rhapsody, totem, etc.) just don't seem to work.  I think that I should install a lighter weight version instead and want to know what steps would be to do that. It's a dual boot system with Windows 2000. Do I just download the xbuntu iso and run through the install process? OR is there another way?
Thanks,
Erik

---

### Post by meng on 2007-02-18
Another way is to:
sudo apt-get install xubuntu-desktop
look here for cleaning up non-Xubuntu packages:
[www.psychocats.net/ubuntu/purexfce](www.psychocats.net/ubuntu/purexfce)

---

### Post by solar george on 2007-02-18
You might want to keep the gnome administration utilities - e.g. the network manager.

---

### Post by erikaaboe on 2007-02-18
Thanks. However, when I run the apt-get to install the xbuntu-desktop, I get the following error: 

me@mine:~$ sudo apt-get install xbuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xbuntu-desktop

I guess that I need to configure apt-get to look elsewhere?

Thanks,
Erik

---

### Post by Maestro23 on 2007-02-18
> **erikaaboe said:**
> Thanks. However, when I run the apt-get to install the xbuntu-desktop, I get the following error: 

me@mine:~$ sudo apt-get install xbuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xbuntu-desktop

I guess that I need to configure apt-get to look elsewhere?

Thanks,
Erik

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Do you have extra Repositories enabled?: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

** Good catch on the typo by bobbob94:)

---

### Post by bobbob94 on 2007-02-18
This might just be a typo in your message but the xfce version of ubuntu is called xubuntu, not xbuntu, so if you're trying to install xbuntu-desktop thats probably your problem ;)

---

### Post by erikaaboe on 2007-02-18
Yep, it was the typo! No matter how good the OS, it just does what you ask! It is now chugging away getting the files. Thanks to all and I'll clean up the Gnome apps with the linked tutorial from psychocats.

Sort of reminds me of the "casper-cow" label on a USB stick. I read it in a book somewhere and could not figure out why I was unable to get a persistent session with a live CD. Turns out that the label needed to be "casper-rw" so it never worked no matter how many times I tried.

Thanks, all.

---

