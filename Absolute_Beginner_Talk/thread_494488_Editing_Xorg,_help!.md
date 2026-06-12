---
title: "Editing Xorg, help!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Hyrup on 2007-07-06
I have a dual-boot vista/unbuntu system, and I recently added something in my xorg.conf file that apparently shouldnt be there..and now I can't boot into Unbuntu because of the x-server.

My question is, is there some way I can open the xorg file, edit and save it...all without connecting into X itself?

---

### Post by felicity on 2007-07-07
yes, I use nano but you can use other console editors too.

If you have it installed just 'nano /etc/X11/xorg.conf' from the command line. If you don't, you should be able to install it with apt-get from the command line.

---

### Post by Hyrup on 2007-07-07
Fixed it, thanks :popcorn:

---

