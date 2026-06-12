---
title: "How do you navigate directories???"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-29
So I'm a linux noob and I'm having trouble navigating. I need to navigate to **/media/EX HDD/ubuntu-7.10-alternate-i386.iso**. Here's what I did:

ubuntu@ubuntu:~$ cd /home
ubuntu@ubuntu:/home$ cd /media
ubuntu@ubuntu:/media$ cd /ex hdd
bash: cd: /ex: No such file or directory

I don't get it. :confused:

---

### Post by philinux on 2007-11-29
You need "" marks round it cos of the space in one of the directories.

---

### Post by wheredidrealitygo on 2007-11-29
spaces in command lines need a \ (forward slash)

```
cd /media/EX\ HDD/
``` will get you there, no matter from where, you don't have to cd through one directory at a time if you know the next one.

---

### Post by evilregis on 2007-11-29
Hehehe, you answered your own question.  You need to navigate to:

```
ubuntu@ubuntu:~$ cd /media/EX\ HDD/ubuntu-7.10-alternate-i386.iso
```

*note the slash before the space

---

### Post by forestpixie on 2007-11-29
linux doesn't enjoy spaces it seems - and there's also case sensitivity

you need to use \ where there's a space - tab can autocomplete 

have a look at this [http://ubuntuforums.org/showthread.php?t=273621](http://ubuntuforums.org/showthread.php?t=273621)

---

