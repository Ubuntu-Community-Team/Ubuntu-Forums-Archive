---
title: "if there is aproblem between rpm and Ubunt"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by black_ice on 2006-12-14
hello all 

i am using ubuntu 6.10 and i have aproblem with rpm files when i want to make install to an .rpm files nothin happened and there is no mannual pages for arpm !!!!!!!!!!!!!!!!!!!!!!1

---

### Post by taurus on 2006-12-14
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install alien
alien **filename**.rpm
sudo dpkg -i **filename**.deb
```

---

### Post by Sef on 2006-12-14
Ubuntu uses .deb, not .rpm.  You need to convert rpms to debs with alien.

Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by BarfBag on 2006-12-14
Ubuntu is based on Debian, which uses .deb instead of .rpm.  If you can, it's best to find the .deb version and install it using this command:

> sudo dpkg -i packagename.deb

If you can't find a .deb, you can either compile from source (semi complicated), or use alien to convert the .rpm.

---

### Post by black_ice on 2006-12-14
thanx for great support but i did that with m realplayer.rpm and it located now at /usr/local/Realplayer and i cannot get it work :(

---

### Post by taurus on 2006-12-14
```
/usr/local/Realplayer/realplayer
```

---

### Post by black_ice on 2006-12-14
thanx thanx thanx :) 

the last thing i want to ask about how to pind it to applications menu 

and thanx alot

---

### Post by taurus on 2006-12-14
You can create a shotcut in the panel!

Place a cursor on the panel and click

Add to Panel -> Custom Application Launcher 

Name:  RealPlayer
Command:  /usr/local/Realplayer/realplayer

then click OK to save it...  So if you want to run it, just click on it from the panel!  It's fast and easy.

---

### Post by macogw on 2006-12-14
> **black_ice said:**
> thanx thanx thanx :) 

the last thing i want to ask about how to pind it to applications menu 

and thanx alot
Go to Alacarte Menu Editor (either right click the menu at the top and click "edit menu" or go Applications > Accessories > Alacarte), click on "Sound and Video", then click "add new item"  Type "realplayer" into the command part, "Real Player" into the name part, and grab an icon for it.

---

### Post by az on 2006-12-14
> **taurus said:**
> ```
/usr/local/Realplayer/realplayer
```

Using add-remove programs, add the commercial applications repository and install realplayer from the ubuntu archive.

---

