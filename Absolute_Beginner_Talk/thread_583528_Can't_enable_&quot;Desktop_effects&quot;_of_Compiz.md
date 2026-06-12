---
title: "Can't enable &quot;Desktop effects&quot; of Compiz in Gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-10-20
I'm running a Geforce FX 5200 and have enabled the "restricted drivers" however, when I attempt to enable desktop effects, it tells me it can't do it.  (That's what it says).

Also, when running compiz I get the following error:

/var/log$ compiz
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

In my xorg.conf file i've got:

Driver "nvidia"   

As opposed to Driver "nv"  so it looks like I'm running the restricted driver.

When running Feisty I had no problem at all running beryl and using the effects.

I did have some problems when upgrading to Gutsy, and had to recompile the nvidia drivers, and wonder if that's what went wrong.  (I downloaded the .run file from the Nvidia site)


I installed the linux-restricted-modules for the kernel for apt-get.  Now I can run compiz, and I appear to be able to do *some* things (The sliding desktops now work).

However, when I run Desktop effects, and click on "Enable Desktop Effects" the screen blanks, and asks me if I want to keep the settings.  If I select yes, the enable desktop effects button is still there, and if I click no, the enable desktop effects button is still there.

When I attempt to run the compiz settings manager, nothing happens.  I expect I'm getting an error and not seeing it.

I've uploaded my xorg.0.log because I bet its in there somewhere, and I'm just not seeing it.

Anyone have any ideas?

---

### Post by mohnkern on 2007-10-20
This might provide some more information:

When I run ccsm from the terminal:

raceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


There's probably something that needs to be installed.

---

### Post by mohnkern on 2007-10-21
Bump.

---

