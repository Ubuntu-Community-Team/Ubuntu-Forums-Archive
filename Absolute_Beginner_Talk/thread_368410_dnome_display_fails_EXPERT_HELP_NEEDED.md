---
title: "dnome display fails EXPERT HELP NEEDED"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-02-23
Hi
i installed ubuntu many dif times and everytime 
if i login from the generic mode normally it starts and when the gnome display starts(after giving user name psswd) you can only see the ubuntu background, cursor responds moving but no taskbars and you cannot do anything

if i login in recovery mode everything is fine, while in recovery mode if i logout>exit and then normally start the session, it starts ok

My graphics card is an ATI RADEON 9600, installed fglrx driver
i get normally:
evan@evan-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

and
evan@evan-laptop:~$ glxinfo | grep direct
direct rendering: Yes


I even installed beryl when i try to start it the cube works, spins but as previously you can only see backgrounds no taskbars

Note: that if i installe kubuntu (KDE enviroments, everything works fine)
So my conclusion is that the gnome fails but why????

CAn anyone please Help?
Many Thanks

---

### Post by linux_kid on 2007-02-23
Well, if apt-get is failing as well as gnome-panel && nautilus, then this is a little more serious than stated.  

When in recovery mode, does the following script work?
```
sudo apt-get install kubuntu-desktop
```
This is because you said you wanted KDE :(

---

### Post by evkefalas on 2007-02-27
tried that and got:
evan@evan-laptop:~$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libseom seom beryl-plugins-unsupported libakamaru0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


thnaks for helping here
any ideas?

---

