---
title: "Gimp 2.2 Help File, IBM T22"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Phil Baxter Jr. on 2007-06-25
Downloaded Gimp 2.2 program, installed in IBM T22.  Seems initially to run OK.  But, ie., but there were no Help files.  Located, downloaded Gimp-Help-2.0.12.tar.gz on desktop.  

Not able to install help tar.gz with install programs, or "tarball" command on either of two terminals.

Have extracted Gimp-Help-2.0.12 folder, also to desktop. Now totally confused how to install the help files.  Know tarball terminal instructions fail.  Not able to understand install in help files.

Would appreciate assistance, have spent losts of time and begin to understand why others say putting ubuntu 7.04 on a machine is "tricky".

Thanks,   Phil B

---

### Post by Brucevdk on 2007-06-25
Downloading files outside of the repositories is something you should only do as a "last resort" kind of thing.

Boot up Synaptic (System -> Administration -> Synaptic Package Manager) and search for *gimp-help* (as name) and install those files (gimp-help-common, gimp-help-en) or at the terminal use:
```

sudo apt-get install gimp-help-en

```

After doing so you should be able to access the manual through the help menu in The GIMP.

---

