---
title: "couldn't find package firestarter"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Radovitch on 2007-01-13
Hi,
On attempting to install firestarter on 6.06LTS using the sudo apt-get install firestarter command the terminal's answer after reading the package lists and building the dependency tree is: couldn't find package firestarter. It is not in the package manager and I do have the official ubuntu DvD in the drive and working. I tried using the update manager on the chance that this might help but everything is uptodate.

Any help greatly appreciated.

---

### Post by Pobega on 2007-01-13
What are the contents of your sources.list file?

---

### Post by jvc26 on 2007-01-13
It could be that you havent enabled the extra repositories: check this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
Il

---

### Post by Radovitch on 2007-01-13
Sorry, but as I'm still new to the whole Linux concept I need to ask where I can find this list.

---

### Post by taurus on 2007-01-13
Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Radovitch on 2007-01-13
Thanks, Illuvator

Enabling the extra Universe and Multiverse repositories in the package manager did the trick. Not only firestarter but a bunch of other updates came down the pipeline as well. I would never have found that on my own.

---

### Post by jvc26 on 2007-01-13
No problem :)
Il

---

### Post by highvoltage on 2007-01-13
You can also add the Universe component from the GUI from System -> Administration -> Software sources.

Have fun!

---

