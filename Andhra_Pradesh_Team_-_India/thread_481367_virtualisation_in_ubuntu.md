---
title: "virtualisation in ubuntu"
date: 2007-06-22
forum: Andhra Pradesh Team - India
---

### Post by nagarjunareddy on 2007-06-22
Dear friends,
 How do I run a win98 application on ubuntu?
What tools are available?
Where do I find them?
-Nagarjuna.

---

### Post by SaitoSan on 2007-08-05
You could try using wine, windows emulator,  which you could install from synaptic package manager. You might need to change your repository which this website (assuming u're using feisty) tells you how:
```
http://ubuntuguide.org/wiki/Ubuntu:Feisty
```

Go to System -> Preference -> WIne Configuration to change the targeted windows to windows 98.  Then from the command line run:
```
wine application-name.exe
``` 

Or alternatively you could use virtualisation like VMWare. I've never tried this, but you'll need a copy of windows 98 cd.

Hope it helps :)

---

### Post by bharadwaj on 2008-01-26
seamless virtuallisation is the best , this emulating and virtuallising are good but you can't say everything runs in them and the later process is very memory intensive. Ide suggest you to get on and go for seamless virtualisation using Vmware or Vbox Quemu is eually good but you need to be a bit more geeky than these them.
OR Ide suggest you if you think that this whole crap is just the pain in *** go for wine or crossoever the only option you have got.

---

