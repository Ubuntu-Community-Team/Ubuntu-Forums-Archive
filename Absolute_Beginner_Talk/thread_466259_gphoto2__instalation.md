---
title: "gphoto2  instalation ?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by gulmer on 2007-06-06
Downloaded gphoto2 newest version to load my camera model into the system settings digital camera config.  How do I get the folder named "gphoto2-2.3.1 tar.gz" into the system settings?
Thanks, Gene

---

### Post by xopher on 2007-06-06
You're sure the gphoto2 included in the repositories do not support your camera?

The configuration file is probably located inside the tar.gz-file, which is a compressed archive, just like zip-files, just open it with file-roller and search for the configuration file you need.

---

### Post by gulmer on 2007-06-07
> **xopher said:**
> You're sure the gphoto2 included in the repositories do not support your camera?

The configuration file is probably located inside the tar.gz-file, which is a compressed archive, just like zip-files, just open it with file-roller and search for the configuration file you need.

The gphoto2 version that is loaded is 2.1.6 and my camera model is not listed. The new version is 2.3.1 and has my camera model. Is there a way to upgrade the existing version with out having to download the whole new version? and if not, what is the file-roller and how do I know what config. file I need and what do I do with it?
Thanks for your reply

---

### Post by zvacet on 2007-06-07
```
sudo aptitude install p7zip p7zip-full rar unrar
```

After this just right clcck on the tar.gz package and select** unpack here**.If you need to compile you must have built-essential,so

```
sudo aptitude install build-essntial
```

go to the untared folder and find **read me** or **install file** to see if there is any dependencies needed before you start to compile.Usual commands for compile 

1.  ./configure
2.  make
3. sudo make install

This is in most cases but to be sure this is correct in your case it is important to look in **read me** and** install** files.

---

