---
title: "Ubuntu Studio and Xorg Configuration"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-14
I had Ubuntu Feisty 32 bit installed and I used repos to install Ubuntu Studio on my system with an NVidia 7600GT.
I restarted my computer and it said it couldn't load the NVidia kernel and that it found the screen, but no usable configuration.
What can I do?

---

### Post by MetalMusicAddict on 2007-06-14
Your missing the kernel modules. Do this in a terminal: **sudo apt-get install linux-lowlatency**

---

### Post by dannymichel on 2007-06-14
Thanks man. I really appreciate that.

---

