---
title: "Unpacking .rar files"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by HaemoLacria on 2008-01-29
Does anybody know how to easily unpack .rar files on Ubuntu

---

### Post by amo-ej1 on 2008-01-29
by installing unrar ? 

```

e@lape:~$ apt-cache search unrar
unrar-free - Unarchiver for .rar files
unrar - Unarchiver for .rar files (non-free version)

```

---

### Post by jeffus_il on 2008-01-29
Make sure you have "unrar" installed, then use the archiver to extract. The association should automatically update with the install and clicking on a rar archive in Nautilus should do the trick.

---

### Post by chris200x9 on 2008-01-29
sudo apt get install rar

edit: it's in synaptic I'm assuming that's the command, if not do the gui synaptic.

---

### Post by usater on 2008-01-29
there is a package u need to install to unrar Rar file 

u'll get in ubundu  software channel

otherwise u'll have to install Wine and then Winrar.

this take more download contant but faster than normal archiver in linux

but if not properly monitored it will eat ur hard disk space by temporary files created in ~/.wine folder

Al lthe best:)

---

### Post by HaemoLacria on 2008-01-29
It says: archive type not supported

---

### Post by amo-ej1 on 2008-01-29
could you open a console and type  'file your_rar_file.rar'

could be that there's a version mismatched, or someone gave the file a wrong extension.

---

### Post by chris200x9 on 2008-01-29
> **HaemoLacria said:**
> It says: archive type not supported

I had the same problem did you install rar via synaptic cuz thats all I did :)

---

### Post by zvacet on 2008-01-29
```
sudo apt-get install rar unrar p7zip p7zip-full
```

Right click on file and select **unpack here**.

---

