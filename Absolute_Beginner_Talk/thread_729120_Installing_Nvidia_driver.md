---
title: "Installing Nvidia driver"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by sUBHO on 2008-03-19
Hi i am absolutely new to ubuntu/linux. i am using linux 7.04 and i have nvidia 7600 driver.
The problem started when i tried to enable compiz by going to System ->Preferences->Desktop Effects..... and then I "Enable Driver" but nothing happens

then i try  System ->Administration->restricted drivers manager
i find that nvidia gpu is not enabled! but even if i enable it nothing happens...nothing is downloaded

then i try to install the driver using Envy. but the error it gave was "dependancy is not satisfiable"

when i use "sudo apt-get install nvidia-glx nvidia-kernel-common"
it shows
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate


so what to do next?
(p.s. i went through the other posts but did not get them fully):confused:

---

### Post by NR1224 on 2008-03-19
did u try synptic? maybe the driver is in there.

---

### Post by StOoZ on 2008-03-19
try "envy" ... its a tool for installing gfx drivers.

---

### Post by donnyblaze1 on 2008-03-19
To get the absolute latest nvidia drivers installed...[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

Good luck!

---

### Post by Daveth on 2008-03-19
Envy better sourced from here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

works a treat for me and my GT7900

---

### Post by sUBHO on 2008-03-20
Actually I discovered the solution myself :lolflag:

Its quite simple. Just go to Synaptic PackMan and add  nvidia-glx-new to be downloaded....and voila!! u dont need envy or anytjing else.

---

### Post by jaimerod on 2008-03-20
Thanks that works great for me.

---

