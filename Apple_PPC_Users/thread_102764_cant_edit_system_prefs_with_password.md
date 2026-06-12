---
title: "cant edit system prefs with password"
date: 2005-12-12
forum: Apple PPC Users
---

### Post by macm10 on 2005-12-12
this is huge problem, i cannot get into any of my networking (or any) system prefs. i click administator mode, enter in my pass. then a few seconds later it loads up the same screen with everything greyed out. this is huge problem beacuse i have important work on this system i need to send out via email tonight!

---

### Post by amohanty on 2005-12-12
try:

```
sudo gnome-nettool
```

In the first tab - Devices - select eth0 or your NIC name and click configure.

Does that work?

---

### Post by macm10 on 2005-12-13
no :( it does not work(it says command not found). in KDE when i go to system prefs. and go to say network settings, it has everything greyed out and a "admin. mode" button at the bottom. i click the button and i see:
a: a blank box with a red boarder around it
b: it ask for a password then resets it self to the greyed out window

if i end up switching back to Ubuntu with gnome i want to know what the equivilent to kinfo is. the device manage in gnome never told me ram/cpu sepc.

---

### Post by amohanty on 2005-12-13
I am sorry, I didnt realize you were using kubuntu, unfortuntely I dont use kde so cant help you there. The command I gave you was for gnome. For cpu system specs, I think, Applications->Accessories->System monitor is the tool to look at.

HTH

Edit: Can you post a screenshot by any chance?

---

### Post by macm10 on 2005-12-13
i got the proc thing all settled out, i cannot post a screen shot beacuse of the fact that i cannot edit system prefs. it is completly isolated, i have even tryed mounting a usb pin drive, nothing. i would post a screen shot if i could.

---

### Post by teaker1s on 2005-12-13
it's a bug use 
'sudo kcontrol'

---

### Post by amohanty on 2005-12-13
Just saw this:
[http://ubuntuforums.org/showthread.php?t=103101](http://ubuntuforums.org/showthread.php?t=103101)

oops.. teaker1s already posted the solution. damn gotta learn touch typing.

---

