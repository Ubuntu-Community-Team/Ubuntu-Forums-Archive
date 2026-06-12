---
title: "Navigating folders with the terminal [Resolved]"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by mcz0119 on 2007-02-24
I downloaded a couple of files to my home directory. When I try to access them thru the terminal it says that the file or folder doesn't exist. See below:
miguel@ubuntu:~$ ls
bin                               key.gpg.asc.5
Desktop                           NATURE-Autumn_1024x768.jpg
Examples                          NATURE-RedSaturday_1024x768.jpg
GNOME-GnomeBlueBlur_1024x768.png  NATURE-RockIslandInLakeNasser_1024x768.jpg
GNOME-GNOMEflipped_1024x768.png   Network Key
key.gpg.asc                       Nozomi
key.gpg.asc.1                     Photos
key.gpg.asc.2                     PicasaDocuments
key.gpg.asc.3                     vmware
key.gpg.asc.4
miguel@ubuntu:~$ cd /nozomi
bash: cd: /nozomi: No such file or directory
miguel@ubuntu:~$ 

I tried the other slash, without the slash, without the cd, without the cd or /. Not sure what I'm doing wrong.

Thanks for any help.

---

### Post by equal on 2007-02-24
Case sensitive. Did youtry typing cd Nozomi?

---

### Post by aysiu on 2007-02-24
Not only is it case-sensitive, but it's also a *sub*directory--so you shouldn't put a slash in front of *nozomi*.

equal's right--it should be ```
cd Nozomi
``` not ```
cd /nozomi
```

---

### Post by mcz0119 on 2007-02-24
Thanks. I knew it had to be something simple.

---

