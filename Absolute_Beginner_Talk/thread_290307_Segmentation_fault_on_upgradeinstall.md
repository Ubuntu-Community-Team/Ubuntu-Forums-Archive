---
title: "Segmentation fault on upgrade/install"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Amelia on 2006-11-01
(First post)

Installed LTS version (DD) for AMD64. All well for a week, but the upgrade stopped working. This list of modules to be upgraded is piling up.

Every time I run the auto-updater nothing happens. I think it more informative to say that when I try to apt-get upgrade, the show stops at segmentation fault.

The whole situation emerged first time with ffmpeg upgrade. Now I can't remove it or anything else.

Tried looking the forum, but didn't find out what to do. Any ideas.

//A

---

### Post by Amelia on 2006-11-05
THis is basically what happens after apt-get upgrade

(Reading database ... E: Sub-process /usr/bin/dpkg received a segmentation fault.

---

### Post by justifier on 2006-11-05
try running 

sudo apt-get update

---

### Post by Amelia on 2006-11-05
Done. No help.

The update list keeps piling up and I can not install or remove anynthing.

---

