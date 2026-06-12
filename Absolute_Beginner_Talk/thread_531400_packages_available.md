---
title: "packages available"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by emanresu on 2007-08-21
this is probably a redundant question, but i've spent an hour looking at other forum posts and haven't had any luck yet, so sorry...

how  do i determine what applications/packages are already on my computer, so i don't have to try to download something again? for example, i want to erase a CDRW and burn something else to it, but when i look in Applications>Sound&Video there are:
Movie Player
Rhythmbox
Serpentine audio CD creator
Soundjuice CD extractor
sound recorder

and none of those apps want to erase my disk. besides this, i'd like to know what else is around here.

---

### Post by WebSiteGuru on 2007-08-21
You can go through System > Administration > Sympatic and search for those items. It will be taged in green if it is installed. There are also other way like add/remove programs under Applications.

---

### Post by Paulmd on 2007-08-21
> **emanresu said:**
> this is probably a redundant question, but i've spent an hour looking at other forum posts and haven't had any luck yet, so sorry...

how  do i determine what applications/packages are already on my computer, so i don't have to try to download something again? for example, i want to erase a CDRW and burn something else to it, but when i look in Applications>Sound&Video there are:
Movie Player
Rhythmbox
Serpentine audio CD creator
Soundjuice CD extractor
sound recorder

and none of those apps want to erase my disk. besides this, i'd like to know what else is around here.

Got to add/remove programs, and look for K3b.

---

### Post by p_quarles on 2007-08-21
Easy way to get a text file that lists all your installed packages:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```
Then:
```
cat package_list | less
```to see what's installed on your system.

---

### Post by Hobo Joe on 2007-08-21
I really like Gnomeburner. 
To install, paste this into the terminal:
```

sudo aptitude install gnomeburner

```

---

### Post by mikewhatever on 2007-08-21
> **emanresu said:**
> this is probably a redundant question, but i've spent an hour looking at other forum posts and haven't had any luck yet, so sorry...

how  do i determine what applications/packages are already on my computer, so i don't have to try to download something again? for example, i want to erase a CDRW and burn something else to it, but when i look in Applications>Sound&Video there are:
Movie Player
Rhythmbox
Serpentine audio CD creator
Soundjuice CD extractor
sound recorder

and none of those apps want to erase my disk. besides this, i'd like to know what else is around here.
You can search for a package in Synaptic. It would be marked green if installed. You can also use a filter to see the list of all installed packages. I am not sure if that question is related to the program names and erasing CDs issue. Graveman or Brasero can both do that.

---

### Post by emanresu on 2007-08-22
thanks to all of you. my question has been answered.

---

