---
title: "Flash Problem.."
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by ech0^ on 2007-05-04
Hello i am having a problem running games on a website [**LINK HERE**]("http://www.miniclip.com/games/robot-rage/en/") to see what it uses.


I'm sure it is flash and i have tried doing the following : 

```
sudo aptitude install flashplugin-nonfree
```

that didn't work so i tried the following : 

```
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc

Edited : FIREFOX_DSP="NONE" 
To :  FIREFOX_DSP="aoss"
```

Yet i still am unable to get flash working? Any ideas what i have done wrong?

---

### Post by ech0^ on 2007-05-04
anybody?

---

### Post by starcraft.man on 2007-05-04
Miniclip and other game sites like this use shockwave, and Ubuntu = Linux = No Shockwave.

No solution for this problem yet.

Have to look elsewhere to play games.

---

### Post by ridgeone on 2007-05-06
Not only games, but I use a DoD E-Learning website that uses Shockwave for some of their courses (specifically Rosetta Stone Language courses). I cannot access these courses from Linux. Still have to dual-boot until a Linux Shockwave solution arises.:(

---

### Post by eldepeche on 2007-05-06
If you're on x86, you can just download the .tar.gz from the Adobe website and install that. I think that's what the APT package does, but they move the file every once in a while.

---

