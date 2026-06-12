---
title: "Kicker"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by 5ER on 2007-04-14
I have an amd64 processor and an amd64 installation with kde.
I tried to install [kickoff]("http://www.kde-look.org/content/show.php/Kubuntu+with+Suse+Kickoff+Edgy+Elf+6.10?content=50240") i386 with --force-architecture.
Now when I try to reinstall, install,... kicker all is usual, but in some part of output it says ```
Unpacking kicker (from .../kicker_4%3a3.5.6-0ubuntu1~edgy1_amd64.deb) ...
Replaced by files in installed package kicker-kickoff ...
```And when I run kicker it says ```
kicker: error while loading shared libraries: libkonq.so.4: wrong ELF class: ELFCLASS64

```
This really bothers me, as I now have no kicker... :(
Help me, please :(

---

### Post by CompShrink on 2007-04-14
From my understanding, that is a i386 only package right now, it won't work on an amd64 install.

So, uninstall kickoff and re-install kicker, and hopefully you should be fine. Post back here if you still have problems.

---

### Post by 5ER on 2007-04-14
Well, it says Couldn't find any package whose name or description matched "kickoff"
and also Couldn't find any package whose name or description matched "kicker-kickoff"
as is also possible to be called.

If I try to uninstall using the deb file with dpkg, it says```
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by 5ER on 2007-04-15
I tryed uninstalling kickoff with Kpackage, but I saw it is not installed, only some files are still there. So, I installed kickoff using Kpackage and then uninstaled it with Kpackage and now it's completely gone. Now I just reinstalled kicker with aptitude. :)

---

