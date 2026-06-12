---
title: "installing xfi audio drivers"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by orion13 on 2008-03-10
Try to install the ALSA drivers I got from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

With the instructions I found from [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

When I run the sudo ./configure line I get:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

What am I doing wrong?

---

### Post by LuisGMarine on 2008-03-10
Follow this guide instead, much much easier!

[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by jrusso2 on 2008-03-10
> **orion13 said:**
> Try to install the ALSA drivers I got from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

With the instructions I found from [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html)

When I run the sudo ./configure line I get:

checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

What am I doing wrong?

I was wondering if you have installed the build-essentials package?

---

### Post by orion13 on 2008-03-10
> **LuisGMarine said:**
> Follow this guide instead, much much easier!

[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)


After the reboot and I try to do the sudo ./alsa_2.sh I get this error



cp: cannot stat `/lib/modules/2.6.2*/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
cp: cannot stat `/usr/src/alsa/alsa-driver*/modules/*': No such file or directory

---

