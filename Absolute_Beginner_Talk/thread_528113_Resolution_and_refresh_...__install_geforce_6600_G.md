---
title: "Resolution and refresh ...  install geforce 6600 GT ? Yahoo messenger ...  problem"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by baovucuongphong on 2007-08-17
I use Ubuntu 7.04

1/ When I choose the monitor´s resolution like 1024 x 768, 1024 x 1280, ... the refresh only has 55 HZ, 56 Hz to 66 Hz, not as the default in windows 85 Hz with 1024 x 768 

2/Everybody can help me to install my VGA card, it´s Geforce 6600 GT. I search and find this thread, ```
http://ubuntuforums.org/showthread.php?t=528035
```

and install this file```
 http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu1_all.deb
```

but don´t know how to know whether my VGA driver was installed.
3/ I go to the Y! site to download yahoo for ubuntu , here : ```
 http://messenger.yahoo.com/?wm=n
``` and install this file 
**dpkg -i ymessenger_1.0.4_1_i386.deb **

and see [COLOR="Red"]error : Dependency is not satisfiable : libssl0.9.6[/COLOR]

4/ I can´t use my Soundmax 5.1 (B 30) although I installed the file **realtek-linux-audiopack-4.06a.tar.bz2** that downloaded from the realtek site .  I can only listen the music by microphone 

How to solve ? 

Thanks a lot

---

### Post by ddrichardson on 2007-08-17
Gaim is installed by default and supports the Yahoo protocol. When installing by deb file you need to install any dependancies - in this case libssl

---

### Post by baovucuongphong on 2007-08-17
I installed libss0.9.8 means higher than 0.9.6 , but still recieved that error

---

### Post by ddrichardson on 2007-08-17
Not neccesarily - if its looking for a specific version rather than higher than.

---

