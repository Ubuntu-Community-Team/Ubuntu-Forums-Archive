---
title: "confusion in synaptic package manager"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by TheGreenMutville.edut on 2006-05-01
hey i was opening the synaptic package manager to install VLC and i got a message saying

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_unstable_main_binary-i386_Packages) - stat (2 No such file or directory)

what does this mean???

---

### Post by aysiu on 2006-05-01
Mixing Debian and Ubuntu repositories will eventually lead to system breakage.

VLC can be installed using Ubuntu repositories. For instructions on obtaining extra Ubuntu repositories, go here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then copy and paste these instructions to a terminal (Alt-F2, *konsole*, in KDE; Alt-F2, *gnome-terminal*, in Gnome--to get a terminal): ```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by TheGreenMutville.edut on 2006-05-02
hey thanks that made the message go away,  a friend of mine told me when downloading ubuntu can be considered debian is this not true??

---

### Post by Borniet on 2006-05-02
[QUOTE=TheGreenMutville.edut]hey thanks that made the message go away,  a friend of mine told me when downloading ubuntu can be considered debian is this not true??[/QUOTE]

Ubuntu is a Debian-ish distribution, based on, following the same principles more or less (more less then more). But they are not the same distributions.

---

### Post by TheGreenMutville.edut on 2006-05-02
ok thanks guys

---

