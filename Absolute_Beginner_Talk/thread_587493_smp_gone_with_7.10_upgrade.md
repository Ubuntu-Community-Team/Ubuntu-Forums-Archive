---
title: "smp gone with 7.10 upgrade"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by wdethoma on 2007-10-22
Just upgraded and when I check I only see one cpu. I have two Xeons hyperthreaded so four should appear.  What is recommended?

Thanks

---

### Post by mikewhatever on 2007-10-22
What kernel is in use? Please post the output of uname -r.

---

### Post by wdethoma on 2007-10-24
2.6.22-14-386

---

### Post by mikewhatever on 2007-10-24
That's the problem. It should be 2.6.22-14-generic. Try installing it from the repositories.

---

### Post by wdethoma on 2007-10-24
Thanks, I'll try

---

### Post by wdethoma on 2007-10-24
Tried to find kernel to configure and don't know where it is.  Looked in /boot directory and not there.  Looked in /usr/src and not there.  tried to complie a new one but does not work.  All I need is WHERE is the kernel so that I can do a make menuconfig so that I can set smp.  Any ideas?
 
Thanks

---

### Post by mikewhatever on 2007-10-24
Search for 2.6.22-14 in synaptic.

---

