---
title: "rar/unrar"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-01
I have some files i want to unrar. I have tried to install unrar and rar "sudo apt-get install unrar" but it doesnt work. I have also tried to download winrar for linux but I dont get that to work either. How do I unrar packets?
When I use unrar I get this message: unrar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by unrar)

---

### Post by JamieC on 2007-02-01
What was the result of the command you mentioned?

Anyway, try this:
```

sudo apt-get install unrar-free

```

If it installs successfully, you can use it like so (where <directory> is the directory the archive is within, and <archive> is the name of the RAR archive):
```

cd <directory>
unrar-free -x <archive>

```

---

### Post by Maestro23 on 2007-02-01
.

---

### Post by PurplePenguin on 2007-02-01
> **inspiron said:**
> I have some files i want to unrar. I have tried to install unrar and rar "sudo apt-get install unrar" but it doesnt work. I have also tried to download winrar for linux but I dont get that to work either. How do I unrar packets?
When I use unrar I get this message: unrar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by unrar)

I use the File Roller archive manager to unrar archives.

I think I installed some sort of extra archive formats or something through Automatix, I forget... I'm not sure if you can unrar out of the box or not. :)

---

### Post by glabouni on 2007-02-01
[to install rar and unrar with apt-get]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_RAR_Archiver_.28rar.29") you'll need to enable extra [repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

you can also use [automatix2]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu")

---

### Post by v3ldrinn on 2007-12-29
this is the repository for debian etch

deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) etch main non-free

ubuntu would be something similar... just add the "non-free" entry to the end of what you already have. :)
add it to "/etc/apt/sources.list"

the unrar package works like a charm!
(unrar-free doesn't though... don't know why)

---

