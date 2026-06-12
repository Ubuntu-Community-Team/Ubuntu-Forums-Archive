---
title: "[SOLVED] pommed and streaming in amarok"
date: 2007-09-30
forum: Apple Intel Users
---

### Post by deb on 2007-09-30
Hi, does anyone else face these problems or its only me? ... any clues... hints...
[http://ubuntuforums.org/showthread.php?t=562847](http://ubuntuforums.org/showthread.php?t=562847)

[http://ubuntuforums.org/showthread.php?t=562896](http://ubuntuforums.org/showthread.php?t=562896)

---

### Post by deb on 2007-09-30
well, solved the amarok problem, libxine-ffmpeg works fine.
is compiling pommed is the only option for getting pommed working???

---

### Post by deb on 2007-10-01
Solved.
Pommed was not working because in gutsy the applesmc module does not load automatically during boot. One has to manually pass $sudo modprobe applesmc and then $sudo pommed and everything starts working...

---

### Post by vh1 on 2007-10-03
you can add applesmc to the file /etc/modules
and if you've installed pommed from the repos, it should start itself

---

### Post by deb on 2007-10-04
in gutsy there is no /etc/modules; I found only modprobe.d and modutils.

---

### Post by cyberdork33 on 2007-10-04
> **deb said:**
> in gutsy there is no /etc/modules; I found only modprobe.d and modutils.
There is on both my gutsy systems

---

### Post by JBAlaska on 2007-10-04
[quote="deb"]in gutsy there is no /etc/modules; I found only modprobe.d and modutils.[/quote]

Look for a text file named "modules", not a directory

---

### Post by deb on 2007-10-05
@vh1... first let me thank you for the tip... now it rocks :guitar:.
@JBAlaska... thanks for pointing that out... I am a new ubuntu user...was acually trying to make a soft link of applesmc.ko somewhere in modules /etc/modules dir...should have paid more attention to vh1's post ... on the other hand everything is "file" in *nix isn't it?... he he!!!

---

