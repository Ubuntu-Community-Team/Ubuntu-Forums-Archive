---
title: "Trouble Installing Wine"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Mombie on 2008-03-22
I just installed Ubuntu and i love it, but i cant seem to get wine running, when i get to the final part of the installation "sudo apt-get install wine" it says it has unmet dependencies 
libaudio2. Could someone please help me, I'm a noob :)

---

### Post by PmDematagoda on 2008-03-22
Please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by thisismalhotra on 2008-03-22
Well for starters ... make sure you have all the repositories enabled ... for that open synaptic and look for repositories in one of the menus (I don't remember which menu). Then hit RELOAD in synaptic.

After that search for wine in synaptic and install from there

TC

---

### Post by Mombie on 2008-03-22
The following packages have unmet dependencies:
  wine: Depends: libaudio2 but it is not installable
E: Broken packages


is that the code you needed?

---

### Post by Darganot on 2008-03-22
follow the directions here:

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

---

