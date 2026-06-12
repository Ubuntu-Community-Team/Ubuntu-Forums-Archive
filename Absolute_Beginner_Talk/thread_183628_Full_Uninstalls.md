---
title: "Full Uninstalls"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by veritos on 2006-05-28
I installed xubuntu-desktop using the normal "apt-get install xubuntu-desktop" method.  But when I remove it, it only removes that one package, without any of the other stuff (xfce4, rox-filer, etc.) ](*,) 

Is there a way to delete all of those packages at once?

---

### Post by skippy81 on 2006-05-28
Theres a script here that was kicking around. I havnt tried it, so use at your own risk.

[http://ubuntuforums.org/showthread.php?t=157897&highlight=xubuntu+desktop+remove]("http://ubuntuforums.org/showthread.php?t=157897&highlight=xubuntu+desktop+remove")

---

### Post by hw-tph on 2006-05-28
If you install software using aptitude (as opposed to, say, synaptic or apt-get) you can uninstall the package and all dependancies that it pulled in as well, as long as those dependancies are not required by some other package.


Håkan

---

