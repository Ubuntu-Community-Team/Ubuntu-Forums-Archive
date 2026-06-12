---
title: "Can I get a Linux History Lesson??"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-09-06
I havent been using ubunutu/linux all that long but do have a question.  Most apps are installed by default in:
/usr/bin or /usr

But when I compile programs from source, most want to set a default installation path to:
/usr/local/bin or simply /usr/local

Why is this???  Im sure there was some historical or present significance to this.

---

### Post by Bachstelze on 2007-09-06
The standard for installing user-installed programs on UNIX systems is /usr/local and /usr is for the base system. However, for whatever reason - and don't ask me why, I don't know -, most - if not all - GNU/Linux distributions today install everything in /usr. But the "real" standard remains on source stuff, which installs by default in /usr/local. You can, however, override this when you run the configuration script, like this :

```
./configure --prefix=/usr
```

---

### Post by afonic on 2007-09-06
Have a look here:

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by kevdog on 2007-09-06
Ok thanks for the input.  I guess I will keep with the traditional /usr/local structure.  It seems however most of the instructions for altering files, themes, etc default to the /usr structure so I will just have to keep this in mind.

Its somewhat confusing when you start compiling at first.  The filesystem hierarchy link at least for me didnt do a very good job of explaining anything.

Thanks for the input.

---

### Post by afonic on 2007-09-06
If you understand how it works and not try to compare everything with Windows structure you'll get it very easily. :)

---

### Post by Bachstelze on 2007-09-06
> **kevdog said:**
> Ok thanks for the input.  I guess I will keep with the traditional /usr/local structure.  It seems however most of the instructions for altering files, themes, etc default to the /usr structure so I will just have to keep this in mind.

Actually, it might be better to install in /usr, to make it consistent with the rest of the system.

---

### Post by kevdog on 2007-09-06
Not to be rude, but how is asking why /usr/local vs /usr have anything to do with windows???

Windows installs in c:\program files, where as most things install in /usr, but a lot of the documentation references /usr/local.

---

### Post by BobCFC on 2007-09-06
Some of this stuff goes back more than 30years it doesn't all make sense.  A lot of it is political/religious. There is a good section on 'The Unix Wars' in an online book called the Art of Unix Programming.  Here is [chapter two]("http://www.faqs.org/docs/artu/historychapter.html") on history.  you may want to go backup a level and read some of the philosophy stuff at the beginning too.

There is a from-source distro you can find in that wiki link from afonic called GoboLinux which trys to rewrite the layout with symlinks to the old way.

```

/System
   /System/Settings
   /System/Kernel
/Programs
/User
/Files
/Mount
```

---

