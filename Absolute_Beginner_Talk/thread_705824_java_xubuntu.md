---
title: "java xubuntu"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by BossGreen on 2008-02-23
i've looked at some of the other help pages already, and when i follow the step
sudo apt-get install sun-java6-plugin
after some words scroll up, it says i need to insert a disc. "gusty_gibon) or something like that...
any help?

---

### Post by taurus on 2008-02-23
Edit /etc/apt/sources.list

```
gksu mousepad /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down the window.  

Then run

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by BossGreen on 2008-02-23
um,
i did all those steps, and i still get this message

Media change: please insert the disc labeled
 'Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

---

### Post by taurus on 2008-02-23
Can you post your /etc/apt/sources.list?  Also, did you remember to run

```
sudo apt-get update
```

---

