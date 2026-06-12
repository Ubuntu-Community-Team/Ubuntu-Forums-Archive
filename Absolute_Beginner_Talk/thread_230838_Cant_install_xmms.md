---
title: "Cant install xmms"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-06
when i enter sudo apt-get install xmms it says to me
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  amsn: Depends: tcltls but it is not going to be installed
  xmms: Depends: libglib1.2 (>= 1.2.0) but it is not going to be installed
        Depends: libgtk1.2 (>= 1.2.10-4) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
what should I do?

---

### Post by enetic on 2006-08-06
you have to do the command sudo apt-get -f install to install some extra packages!

---

### Post by Skia_42 on 2006-08-06
It's much more effective to just go to synaptic and install the program there. It automatically tells you what dependencies there are and it installs them. (System >>> Administration >>> Package Manager)

---

