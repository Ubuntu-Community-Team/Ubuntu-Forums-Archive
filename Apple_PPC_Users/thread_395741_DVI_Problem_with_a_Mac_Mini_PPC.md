---
title: "DVI Problem with a Mac Mini PPC"
date: 2007-03-28
forum: Apple PPC Users
---

### Post by veskoteque on 2007-03-28
Hello, everyone.

I have a Mac Mini PPC which I just converted to Ubuntu.  I can not get my Samsung SyncMaster 225bw to show anything connecting it with a DVI cable - most of the time it looks like its not getting any signal at all.  A Compaq MV900 using the VGA/DVI dohickey works fine.   

I dont know if the computer is not puting out digital signal (I dont have an analog cable to test with) or if it is just bad xorg settings (although I cant even get it to drop to console).

help?

thanks!

---

### Post by grazie on 2007-03-29
Try booting the machine with your Desktop CD (Live CD) and the problematic monitor. If it works, make a copy of /etc/X11/xorg.conf for use on the HD installation. You'll may need different kernel modules loaded too (on the HD installation). Get to that later.

---

### Post by veskoteque on 2007-03-29
when I try that - I get the boot: prompt in the beginning, but from the moment I press 'enter' - its all dark.

I wish I had another DVI to test with, or an analog cable to try with this monitor.  

any other suggestions would be great.

---

