---
title: "Xubuntu 7.10 won't upgrade Wine, Firefox"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by angussf on 2007-11-21
New install of XUbuntu 7.10 on an older IBM Thinkpad.  After installing, apt-get update and apt-get upgrade moved Firefox from 2.0.0.6 to 2.0.0.8, but the "Check for Updates" option in the "Help" menu is greyed-out and neither apt-get nor Synaptic will upgrade it to 2.0.0.9.

Likewise I added WINE (using Synaptic) so I could run Pegasus Mail instead of Thunderbird, but WINE installed at version 0.9.4.6 while the current version, released Nov. 9m is 0.9.4.9.

Why won't XUbuntu upgrade these packages?

TIA

---

### Post by Inxsible on 2007-11-21
> **angussf said:**
> New install of XUbuntu 7.10 on an older IBM Thinkpad.  After installing, apt-get update and apt-get upgrade moved Firefox from 2.0.0.6 to 2.0.0.8, but the "Check for Updates" option in the "Help" menu is greyed-out and neither apt-get nor Synaptic will upgrade it to 2.0.0.9.

Likewise I added WINE (using Synaptic) so I could run Pegasus Mail instead of Thunderbird, but WINE installed at version 0.9.4.6 while the current version, released Nov. 9m is 0.9.4.9.

Why won't XUbuntu upgrade these packages?

TIAUbuntu cannot upgrade to packages that are not in its OWN repository. If you check synaptic, you will see that the latest version (for ubuntu) and the installed versions are the same.

When a new software or version is released, it takes some time before the ubuntu developers can get it in to their repositories. This is good actually, since if the new version has some bugs, then you can be safe from it. If however, you absolutely need to have the latest and the greatest, you will have to install it manually.

---

### Post by twiceasworn on 2007-11-21
Synaptic uses a software repository full of debian packages.  If those packages are not updated by the maintainer of said repository then it isn't going to update, because to the package manager nothing is new.  Typically if you want to most up to date version of things you will have to download it from the program's website and compile it.

---

