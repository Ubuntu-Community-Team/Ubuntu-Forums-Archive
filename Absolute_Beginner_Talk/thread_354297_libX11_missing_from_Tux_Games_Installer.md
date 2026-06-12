---
title: "libX11 missing from Tux Games Installer"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2007-02-05
I have this in a different post, but the title doesnt really describe my problem, so Ill try here. :)

I go into my cdrom directory and type source ./setup like the cd tells me and I get this

```
xfce@xfce:/media/cdrom1$ source ./setup
xfce@xfce:/media$ Initialising files
Extracting archive from CD
Uncompressing archive
If you do not see a popup window, then please simply 
untar the files in the install directory and read the 
appropriate README files
/tmp/tuxsetup: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

```

I do have that libx11 file, anyone know what the problem is, or have used Tux Games?

---

### Post by shareMenaPeace on 2007-02-05
Hmm try

System -> Administration -> Synaptic Package manager and search for "libX11", maybe you miss a part from this libery. Checkbox+apply to install it than.

---

