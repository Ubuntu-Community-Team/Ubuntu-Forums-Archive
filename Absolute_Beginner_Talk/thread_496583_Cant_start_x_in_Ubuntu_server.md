---
title: "Cant start x in Ubuntu server?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by knutbert on 2007-07-09
Hi guys! How do install a graphical interface in Ubuntu server? If I try the code below I get an error msg: E: could not find the package kubuntu-desktop. I want to install KDE.

Code:sudo apt-get install kubuntu-desktop

Please help me.
Thanks.
Regards Knut/ Norway.

---

### Post by Cypher on 2007-07-09
The [kubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/kubuntu-desktop") is a metapackage that will bring all the necessary KDE components.

Show us the contents of your '/etc/apt/sources.list' file.

---

### Post by kerry_s on 2007-07-09
first you need to make sure all your repos are on.

```
**sudo nano /etc/apt/sources.list**
```

uncomment the repos, they start with deb

then

```
**sudo apt-get update**
```

then

```
**sudo apt-get install xorg kdm kubuntu-desktop**
```

then reboot(**ctrl+alt+delete**)

---

