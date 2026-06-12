---
title: "ati mobility radeon x1300 driver install"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by gotitatcostco on 2007-02-21
every time I go to install the ati driver during the part of "sh ati-driver-installer-8.33.6-x86.x86_64.run --buildpkg Ubuntu/edgy" it says Can't open ati-driver-installer-8.33.6-x86.x86_64.run. Please help with this.

---

### Post by angryfirelord on 2007-02-21
Try typing **sudo **sh ati-driver-installer-8.33.6-x86.x86_64.run --buildpkg Ubuntu/edgy

---

### Post by gotitatcostco on 2007-02-24
it still says the same thing

---

### Post by msak007 on 2007-02-24
No offense intended, but I'll ask the obvious - is that the file you downloaded, and if so where did you download it to? Are you in the same directory that you downloaded it to? If you're already in a terminal type ls to list the files and confirm you're in the directory and the file is named what you typed. A lot of times I find it easier to list all the files and then copy / paste the name if the filename is long like that one (more room for human error).

---

### Post by shaolyne on 2008-07-17
Hello community,

I can install the package provided by Ati.
However, when the installation is successfully completed, I  cannot access my session again. I always have to come back to the previous configuration with the following settings

[FONT="Courier New"]shaolyne@shaolyne-laptop:~$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
OpenGL extensions:[/FONT]

Has anybody already encountered such an issue with an "ati mobility radeon x1300" or others card ? Has anybody solved it ?

FYI, I tried as well to install these drivers with EnvyNG and the result is the same, impossible to login to my session and I have to restore the previous Mesa drivers...

---

