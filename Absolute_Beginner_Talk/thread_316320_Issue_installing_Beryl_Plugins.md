---
title: "Issue installing Beryl Plugins"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Araelius on 2006-12-10
I have just successfully installed Beryl but for the life of me I can't seem to install plugins for Beryl. When I attempt to compile the file using the "make" command in the terminal I get this error message:

> -e compiling : 3d.c -> build/lib3d.loPackage xrandr was not found in the pkg-config search path.
Perhaps you should add the directory containing `xrandr.pc'
to the PKG_CONFIG_PATH environment variable
Package 'xrandr', required by 'beryl', not found
3d.c:46:19: error: beryl.h: No such file or directory
3d.c:84: error: expected specifier-qualifier-list before 'CompWindow'
3d.c:100: error: expected specifier-qualifier-list before 'CompOption'
3d.c:153: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'windowIs3D'
3d.c:184: error: expected ')' before '*' token
3d.c:244: error: expected ')' before '*' token
3d.c:282: error: expected ')' before '*' token
3d.c:360: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdPaintWindow'
3d.c:466: error: expected ')' before '*' token
3d.c:483: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdPaintScreen'
3d.c:516: error: expected ')' before '*' token
3d.c: In function 'tdScreenInitOptions':
3d.c:562: error: 'CompOption' undeclared (first use in this function)
3d.c:562: error: (Each undeclared identifier is reported only once
3d.c:562: error: for each function it appears in.)
3d.c:562: error: 'o' undeclared (first use in this function)
3d.c:564: error: 'tdScreen' has no member named 'opt'
3d.c:568: error: 'CompOptionTypeFloat' undeclared (first use in this function)
3d.c:574: error: 'tdScreen' has no member named 'opt'
3d.c:584: error: 'tdScreen' has no member named 'opt'
3d.c:588: error: 'CompOptionTypeBool' undeclared (first use in this function)
3d.c:589: error: 'TRUE' undeclared (first use in this function)
3d.c:591: error: 'tdScreen' has no member named 'opt'
3d.c: At top level:
3d.c:599: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
3d.c:623: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdSetScreenOption'
3d.c:662: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInitDisplay'
3d.c:684: error: expected ')' before '*' token
3d.c:695: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInitScreen'
3d.c:742: error: expected ')' before '*' token
3d.c:759: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInitWindow'
3d.c:778: error: expected ')' before '*' token
3d.c:786: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInit'
3d.c:796: error: expected ')' before '*' token
3d.c:802: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdVTable'
3d.c:826: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/lib3d.lo] Error 1


Any help is greatly appreciated, sorry for the noobish question but this is my first time using Beryl and I am not well versed with Ubuntu myself.

---

### Post by daou on 2006-12-10
This doesn't answer your question, but its a workaround.
Trevino at Beryl forums has made a repository with the newest debs for Beryl and its plugins (like 3D world which you tried to compile).

Have a look at the [original thread]("http://forum.beryl-project.org/viewtopic.php?t=56"). Look at beerorkid's post specifically.

---

### Post by Araelius on 2006-12-10
> **daou said:**
> This doesn't answer your question, but its a workaround.
Trevino at Beryl forums has made a repository with the newest debs for Beryl and its plugins (like 3D world which you tried to compile).

Have a look at the [original thread]("http://forum.beryl-project.org/viewtopic.php?t=56"). Look at beerorkid's post specifically.

Wow, thanks again, I will see if it works. :)

---

### Post by daou on 2006-12-10
And if you want to install the gpg key for Trevino's repository, run the following command in your terminal:

```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
```

It won't give you any more warnings about missing gpg keys. By the way, the Grub thing worked, right ;) ?

---

### Post by Araelius on 2006-12-10
> **daou said:**
> And if you want to install the gpg key for Trevino's repository, run the following command in your terminal:

```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
```

It won't give you any more warnings about missing gpg keys. By the way, the Grub thing worked, right ;) ?

Oh yeah, perfect, thanks again I really appreciate it.

---

### Post by Araelius on 2006-12-10
Still getting errors when trying to get other plugins to work though. Would the libpng have anything to do with it?

---

### Post by daou on 2006-12-10
I'm afraid I don't know. The method in the thread (add repositories, apt-get update, apt-get upgrade) worked for me. You restarted X (CTRL+ALT+BACKSPACE)?

---

