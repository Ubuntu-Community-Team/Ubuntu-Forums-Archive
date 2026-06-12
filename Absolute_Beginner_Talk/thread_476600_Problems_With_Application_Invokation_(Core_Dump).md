---
title: "Problems With Application Invokation (Core Dump)"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by lbthrice on 2007-06-17
Hi all,

I wonder if you all have some advice for me...
I am a molecular biology grad student that is trying to completely migrate to Linux because of political, pedagogical and convenience issue.
I love the Kubuntu environment but I have had a very difficult time trying to install and run Cn3D 4.1, which is a molecule-rendering program that is distributed by the National Center for Biotechology Information (NCBI)

[http://www.ncbi.nlm.nih.gov/Structure/CN3D/cn3d.shtml ]("http://www.ncbi.nlm.nih.gov/Structure/CN3D/cn3d.shtml")

This program is vital to my research and it's non-usability status (is non-usability a word??) in Kubuntu is killing me!

I stumbled over this thread

[http://ubuntuforums.org/showthread.php?t=450118]("http://ubuntuforums.org/showthread.php?t=450118")

and it seemed helpful...part of the issue is that the program searches for out-dated png and tiff libraries...I created symbolic links to the updated libraries in feisty as a work around.

my system is completely updated yet I get the message:

```
Illegal instruction (core dumped)
```

when I invoke the Cn3D program.

Does anyone have any suggestions that may help me to resolve this issue??  Has anyone had any success getting this app to work on Kubuntu 7.04??

---

### Post by lbthrice on 2007-06-17
One more thing: might this have something to do with the requirement for 
system-installed shared libraries of GTK 1.2.7 - 1.2.10?

---

### Post by PaulFr on 2007-06-18
See an earlier thread in these forums on CN3D [http://ubuntuforums.org/showthread.php?t=450118](http://ubuntuforums.org/showthread.php?t=450118) for some pointers on what to do. For libtiff.so.3, linking libtiff.so.4 to libtiff.so.3 should work. Hope this helps.

---

