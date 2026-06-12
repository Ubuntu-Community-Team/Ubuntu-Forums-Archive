---
title: "libfontconfig1 is broken"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Aperium on 2007-02-19
Synaptic lists libfontconfig1 as broken and produces a "Could not apply changes! Fix broken packages first." error when I try to reinstall it. 

When I select the "Fix broken packages" option in Synaptic, I get the following errors:
```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

The updater also throws the following error: ```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
``` 

Running "$ sudo apt-get install -f" returns: ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libfontconfig1: Depends: fontconfig-config (= 2.3.2-7ubuntu2) but 2.4.2-1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```


I'm running Ubuntu 6.10, 32 bit version

Help please!

---

### Post by P_Badger on 2007-02-19
When I had this happen to me, I first selected the package in synaptic, then went to the "Package" menu, then selected "force Version". When the box pops up, go to the drop down menu and choose an earlier version.

---

### Post by Aperium on 2007-02-19
> **P_Badger said:**
> When I had this happen to me, I first selected the package in synaptic, then went to the "Package" menu, then selected "force Version". When the box pops up, go to the drop down menu and choose an earlier version.
The "Force Version" option is grayed out, so I can't select it.

---

### Post by Aperium on 2007-02-19
I think I caused the problem by trying to install libfontconfig1 from debian: [http://packages.debian.org/unstable/libs/libfontconfig1]("http://packages.debian.org/unstable/libs/libfontconfig1")

---

### Post by Aperium on 2007-02-19
OK. I'm reinstalling Ubuntu to fix the problem.

---

### Post by Rastan836 on 2007-02-19
Had the same problem just a few mins ago.. 

found this: 

sudo aptitude purge fontconfig-config

here:

[http://ubuntuforums.org/showthread.php?t=327860]("http://ubuntuforums.org/showthread.php?t=327860")



This might be a bit late for you now, as you said you were reinstalling, but good to know for future reference and also for anyone else having the same prob...

---

