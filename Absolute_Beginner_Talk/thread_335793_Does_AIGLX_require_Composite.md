---
title: "Does AIGLX require Composite?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-01-10
Hi

I'm trying to install Beryl.

I'm following the instructions provided here:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

The "How=to install Beryl with AIGLX on Edgy Eft calls for these settings under /etc/X11/xorg.conf:

Seciotn "Extensions"
	Option "Composite" Enable
EndSection

The ATI driver I installed for my Radeon X1600 Pro required me to disable the Composite option. 

Can I enable AIGLX with Composite disabled?

---

### Post by aidanr on 2007-01-10
if you used the fglrx driver then you will need to use xgl, as fglrx does not support compositing

---

### Post by MindRiot on 2007-01-10
Thanks!

I'll undo the changes I made in /etc/X11/xorg.conf, and then follow the xgl tutorial.

---

### Post by hito1 on 2007-01-11
> **aidanr said:**
> if you used the fglrx driver then you will need to use xgl, as fglrx does not support compositing
Is there any alternative to the fglrx driver then?

Thanks. :)

---

### Post by Patrick-Ruff on 2007-01-16
open source drivers.  fglrx does not support aiglx, and aiglx doesn't /require/ a composite, it's just often used with one (there's no point in having it without it more-like.)

you have an ATI card, so you're basically screwed till ATI adds support for aiglx, or something better comes along (i.e. xegl {I know nothing about it, I just hear it's comming out eventually})

---

### Post by mcduck on 2007-01-16
Open source drivers don't provide 3D-acceleration on most new Ati cards. (and thus can't be used if you want to run Compiz/Beryl).

So for us Ati users the only way to go is fglrx & XGL.

---

