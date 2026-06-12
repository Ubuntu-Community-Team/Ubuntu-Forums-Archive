---
title: "ATI Drivers installed (I think), compiz won't work"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by skunkrecords on 2008-02-20
i have an HD2900, and I installed ATI's 64bit drivers. I can open CCC, but when I set the "Visual Effects" to "Normal", it doesn't let me. I'm pretty sure my drivers installed right, but I may be wrong. Any advice?

---

### Post by spiderbatdad on 2008-02-20
not sure what ccc is. Do you mean compizconfig-settings-manager, ccsm? If not, you'll want to install it. It's in synaptic.  There are a number of guides for getting compiz enabled with the ATI card...here is one: [http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

### Post by szymon_g on 2008-02-20
run 

glxinfo | grep direct

in console. answer

direct rendering: Yes

means that you installed them properly

---

### Post by spiderbatdad on 2008-02-20
Unfortunately you need direct rendering for compiz, not the indirect rendering provided by glx. You'll need fglrx or aiglx.

---

