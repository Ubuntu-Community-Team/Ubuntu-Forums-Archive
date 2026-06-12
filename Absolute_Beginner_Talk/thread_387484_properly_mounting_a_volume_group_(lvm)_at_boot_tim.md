---
title: "properly mounting a volume group (lvm) at boot time"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Cruz on 2007-03-18
Hello,

What is the best way to mount a file system from an lvm volume group? I tried adding it to fstab but it doesn't work, probably becasue the file systems are mounted before lvm is actiavted. The only toher idea I have is a boot script bit it doesn't feel clean to me. Any better suggestions?

Cruz

---

### Post by gilgongo on 2007-03-18
This issue, together with the dreaded device permissions problem (it's MY device goddammit - why can only root access it?), is just about the only Ubuntu issue that makes me truly angry. 

As to your problem, I don't know if this might help?

[http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/06/how-to-always-mount-removable-drives-in-the-same-place-ubuntu-6061-610/)

---

