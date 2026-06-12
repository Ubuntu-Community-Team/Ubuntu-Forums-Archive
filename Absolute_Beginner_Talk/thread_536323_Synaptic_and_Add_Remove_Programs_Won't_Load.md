---
title: "Synaptic and Add Remove Programs Won't Load"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Nylink on 2007-08-27
Hello, I'm new to the forums, and Ubuntu in general.

This is kind of a major problem I'm having. Due to a few problems I've had, I have to reinstall libgtk (or, the whole gtk package). However, when I run the commands in Terminal, I get this:

kevin@kevin-desktop:~$ sudo apt-get install libgtk2.0-0 --reinstall
Reading package lists... Done
Segmentation fault (core dumped)

I try to open add/remove, it would open then instantly close. Same issue with Synaptic, it would open and instantly close. I can't remove or add anything, and Terminal only opens half of the time; the other half it would just instantly close.

Any hope for me? Thanks

[Edit}: I now get Reinstallation of libgtk2.0-0 is not possible, since it cannot be downloaded. when I try to reinstall libgtk.

---

### Post by yabbies on 2007-08-28
when did you notice the repos started crashing?
have you completely removed the faulty libgtk?
$```
sudo rm libgtk2.0-0
```
you can get the libgtk from the debian website

[libgtk2.0-0]("http://packages.debian.org/unstable/libs/libgtk2.0-0")

you may have to try a force removal also. I just read that in some cases synaptic will crash if there is a problem with installation of a package

try this

$sudo dpkg --remove --force-remove libgtk2.0-0

---

### Post by schorsch on 2007-08-28
I would suggest not to mix any packages from the debian repos with those from the ubuntu repos especially when such an essentially package is concerned. If needed you should install from [here]("http://packages.ubuntu.com/feisty/libs/libgtk2.0-0").
But as already mentioned this does not solve the problem that the package manager will not run. Perhaps you are running aout of disk space? What is the output of
```
df -h
```

---

