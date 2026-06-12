---
title: "Upgrading Software (Solved)"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by Alev on 2005-12-03
I have a doubt on how to upgrade software to a newer version.  I have been using synaptic to install stuff, so I'm not really sure as to how using .deb files works.
I want to upgrade GIMP from 2.8 to 2.9, which is not available though synaptic.

I dowloaded the .deb file but I would like to know whether i need to uninstall my current version first.  

I'd also want to know if this new gimp version will show up on synaptic, or otherwise how I can  remove it in the future.

Also please tell me if the answer to my question would apply to other programs as well.

Thank you in advance

---

### Post by aysiu on 2005-12-03
Let's suppose you have gimp-2.2.9.deb sitting on your desktop. If you open a terminal and type ```
cd Desktop
sudo dpkg -i gimp-2.2.9.deb
``` GIMP 2.2.9 will be installed and show up in Synaptic under "local or obsolete." You can uninstall it through Synaptic, but you won't be able to upgrade it unless you have a repository source for it... or you have another .deb.

---

### Post by Alev on 2005-12-04
Thanks a lot, that woked great :) 
Now I won't have to refrain from getting newer versions of programs for not knowing what to do.

---

