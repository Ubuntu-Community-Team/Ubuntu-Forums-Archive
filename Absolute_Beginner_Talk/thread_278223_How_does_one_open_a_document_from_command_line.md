---
title: "How does one open a document from command line??"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-10-16
Hi,
I am trying to work more and more from the command line... I just now needed to open an Open Office document and had to reach for the mouse, dig my way down to the desktop where it is located and double click on it... how could I have opened it via the terminal I was working in??
Thanks!

---

### Post by po0f on 2006-10-16
kpm,

```
$ oowrite /path/to/doc
```

---

### Post by kpm on 2006-10-16
> **po0f said:**
> kpm,

```
$ oowrite /path/to/doc
```

When I try that I get "command not found"
But it got me thinking... and I tried 'openoffice /path/to/doc' and that worked.
Thanks!

---

### Post by bukwirm on 2006-10-16
Or "oowrite /path/to/doc &" if you want to continue to use that terminal (the & puts the process in the background, so you get a command prompt back).

---

### Post by kpm on 2006-10-16
> **bukwirm said:**
> Or "oowrite /path/to/doc &" if you want to continue to use that terminal (the & puts the process in the background, so you get a command prompt back).
Thanks, that is good to know.  My CLI does not seem to know what 'oowrite' is though... it does work with 'openoffice' however.

---

### Post by jordanmthomas on 2006-10-16
If openoffice works, use it by all means:
The proper command for writer is
```
oowriter
```
...just in case you cared to know.

---

### Post by morequarky on 2006-10-16
I am by far not an Linux expert but I became familiar with a few things back in college.  I am familiar with bash a little, need to work on bash scripting a little more....anyways.  I use "joe".

"sudo apt-get install joe" should get you a command-line text editor.  It is a whole lot faster and easier for me to use then opening OO, especially for small, quick changes.

---

### Post by jordanmthomas on 2006-10-16
...but can joe even open OOo documents?

---

### Post by Arndt on 2006-10-16
> **jordanmthomas said:**
> If openoffice works, use it by all means:
The proper command for writer is
```
oowriter
```
...just in case you cared to know.

On my computer, it's oowriter2.

If you know the beginning of a command name, but not the end, write what you know in the shell and press Tab twice. It will list all commands beginning like that:
```

$ oo
oobase2          oofromtemplate2  oomath2          oowriter2
oocalc2          oohtml2          ooo-wrapper2
oodraw2          ooimpress2       oopadmin2
ooffice2         oojvmsetup2      ooweb2
$ oo
```

Another good command is 'locate'.

```
$ locate oowrite
/usr/share/man/man1/oowriter2.1.gz
/usr/share/mimelnk/application/x-oowriter.desktop
/usr/bin/oowriter2
$

```

---

### Post by morequarky on 2006-10-16
true, joe does not open OOwriter documents.  Many times when we ask questions on here we direct them to type sudo gedit, which is techically fine, but after some time of learning Linux in general I suggest a migration to joe.

---

