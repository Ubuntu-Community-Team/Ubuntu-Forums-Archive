---
title: "Synaptic Package Manager question."
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by OscarGortez on 2005-10-06
... I installed Ubuntu awhile ago then un-installed it for a few reasons... anyway I'm running it again now... and before I had a question about how to install a program and someone just told me to update my synaptic package manager files and use that to do... anyway does anyone know where i can find the guide to update the files so that the list of programs will be all big and pretty like i had it before?

---

### Post by orev on 2005-10-06
First things first:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

This will show you how to get started with ubuntu and add to your package lists.

Glad your back!

(BTW:  sudo apt-get install PACKAGENAME works very well too)

---

### Post by Ampersand on 2005-10-06
Hi
The instructions for adding all the repositories is here:
[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories). The mirrormax backports are no longer used, so instead of 
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted

```
put
```

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

---

### Post by orev on 2005-10-06
[QUOTE=Ampersand]Hi
The instructions for adding all the repositories is here:
[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories). The mirrormax backports are no longer used, so instead of 
```

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted

```
put
```

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```[/QUOTE]

Oh yeah....forgot to mention the backports update....thanks.

---

### Post by OscarGortez on 2005-10-06
[QUOTE=orev]

(BTW:  sudo apt-get install PACKAGENAME works very well too)[/QUOTE]
:p that'd work if i knew all the package names though... 

and thanks to you both

---

