---
title: "[SOLVED] Can't run thunderbird - libstdc++.so.5 not found"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by BobLand on 2008-01-21
I just installed Gutsy using a clean install.  Copied my home dir from fiesty.  Tried to start Thunderbird but got 

```
./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: 
cannot open shared object file: No such file or directory
```

I tried
```
sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5
```

gcc version 4.1.3 20070929

A search will find libstdc++.so.6 but not ...5.

I downloaded a fresh copy but got the same message.

I'm also having problems installing the driver for my GeForce 8400.  Get 'can't find compiler' errors.  I downloaded but didn't install glibc2.7xxx.  Would this help?

bobland

---

### Post by sumguy231 on 2008-01-21
That package should exist, could you post your /etc/apt/sources.list?

---

### Post by bumanie on 2008-01-21
Have you tried typing the library name into the search function in synaptic?
That sometimes brings the library up and all you have to do is mark it for installation.

---

### Post by BobLand on 2008-01-21
This is the only line NOT commented out.
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

bobland

---

### Post by sumguy231 on 2008-01-21
That would be a problem. Edit it by running:
```
gksu gedit /etc/apt/sources.list
```
And then uncomment the other lines that begin with 'deb'.

---

### Post by BobLand on 2008-01-21
Uncommented as described, rebooted but no difference.
Get same error running tbird and same error trying to install libstdc++5.

Seems like I'm the only one with this problem?

bobland

---

### Post by bumanie on 2008-01-21
Have a look at this post. They seem to have the same issue as you have.
[http://ubuntuforums.org/showthread.php?p=4177290](http://ubuntuforums.org/showthread.php?p=4177290)

---

### Post by BobLand on 2008-01-21
System can't find package libstdc++5.

---

### Post by BobLand on 2008-01-21
Fixed.  Check this thread out!

[http://ubuntuforums.org/showpost.php?p=3599453&postcount=2](http://ubuntuforums.org/showpost.php?p=3599453&postcount=2)

---

### Post by sumguy231 on 2008-01-21
By the way, I forgot to mention that you need to run:
```
sudo apt-get update
```
Before you will be able to install any packages, including libstdc++5.

---

