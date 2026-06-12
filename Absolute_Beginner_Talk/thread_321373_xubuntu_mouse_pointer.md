---
title: "xubuntu mouse pointer"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by timothy_duncan on 2006-12-18
hi all,

im a complete newbie and installed kubuntu6.06 in my old box.  it's a pentium 500MHz, 256 ram.  i was happy kubuntu6.06 installed without much problem.  but i knew before hand that it will be too slow so i installed the xubuntu desktop.  i searched the net and used this command to install xubuntu

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

it installed heaps of stuff and i thought that the only difference between U/K/Xubuntu is the desktop looks..  anyways, after the install, i log back in using xfce for desktop and my mouse pointer is not the traditional arrow but instead a round spinning pointer.  i think this is the equivalent of the hourglass in xfce when the system is processing.  i thought at first that xubuntu is processing something at startup but no, that was actually my mouse pointer, a round spinning one..  any help to get the arrow mouse pointer?  and btw, is the code i used to get and install xubuntu correct?  what's the difference of this command

```
sudo apt-get install xubuntu-desktop
```

from the other command i used

thanks in advance!

---

### Post by jimrz on 2006-12-18
> **timothy_duncan said:**
> hi all,

im a complete newbie and installed kubuntu6.06 in my old box.  it's a pentium 500MHz, 256 ram.  i was happy kubuntu6.06 installed without much problem.  but i knew before hand that it will be too slow so i installed the xubuntu desktop.  i searched the net and used this command to install xubuntu

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

it installed heaps of stuff and i thought that the only difference between U/K/Xubuntu is the desktop looks..  anyways, after the install, i log back in using xfce for desktop and my mouse pointer is not the traditional arrow but instead a round spinning pointer.  i think this is the equivalent of the hourglass in xfce when the system is processing.  i thought at first that xubuntu is processing something at startup but no, that was actually my mouse pointer, a round spinning one..  any help to get the arrow mouse pointer?  and btw, is the code i used to get and install xubuntu correct?  what's the difference of this command

```
sudo apt-get install xubuntu-desktop
```

from the other command i used

thanks in advance!

the 2nd command is part of the 1st...the 1st one updated what you already had followed by downloading and installing xubuntu apt-get and apptitude are 2 ways of using apt to install software. the install part is pretty much the same, but when uninstalling there are differences. you could also have used synaptic (a gui frontend for apt) to do the same job.

the reason you got such a big d/l is that, while ubuntu and xubuntu are at their core the same, they each have a different set of default software included. So, in addition to the xfce WM, you also got the basic set of programs that comes with it. Examples would be Abiword / Gnumeric spreadsheet rather than OpenOffice and Thunderbird rather than Evolution and on down the line. So you now have all the default progs from both and can use any of them in either WM. if you need to free up some space just remove stuff you do not use (Synaptic is the best way to go about this as it will not remove anything that would still be needed as dependencies for stuff that you retai - shared libraries, etc)

---

### Post by timothy_duncan on 2006-12-20
what about the mouse pointer?  anybody out there knows how i can change my mouse pointer in xubuntu.  the pointer is a round spinning icon instead of arrow..

---

### Post by macogw on 2006-12-20
Is there a preferences thing in the Xubuntu menu?  There might be a "mouse" section in there like there is in Ubuntu.

---

### Post by r4ik on 2006-12-20
Settings-mouse settings-cursor.

---

### Post by timothy_duncan on 2006-12-20
in my xubuntu box, there's nothing in xfce settings regarding mouse cursors...  that's why i'm confused..

---

### Post by timothy_duncan on 2006-12-23
i managed to solve my problem.. and my mouse pointer is back to normal..  it turned out that the xubuntu desktop was not completely installed..  i managed to find out thru adept..

---

