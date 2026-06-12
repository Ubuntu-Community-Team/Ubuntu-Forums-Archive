---
title: "how do i run a program?"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-11-14
i installed byzanz from synaptic, but now i dont know how to start it?

any help?

Thanks

---

### Post by benuski on 2006-11-14
The first thing I always try is to go to the command line and type in the name of the program.  That often works.  Alternatively, you can go back to Synaptic, and then click on the installed files, which I think is under the package menu, and find the file name thats in either /bin or /sbin.  Once you know that name, you can create a launcher icon on the panel, if you want.

---

### Post by turbojugend_gr on 2006-11-14
That's a stupid thing, I always thought synaptic's descritpions should name the command needed to start an app...

Anyway since they don't, I try the package name, or/if/else I check /usr/bin I sort files by modification date and here it is the last one is the last one I installed through synaptic ;)

Indeed you should add a menu entry or a launcher for your commonly used apps.

I hope I helped you, Cheers, TJ.

---

### Post by CatKiller on 2006-11-14
> **jinxjinx said:**
> i installed byzanz from synaptic, but now i dont know how to start it?

any help?

**byzanz-record**, [apparently]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=byzanz&version=dapper&arch=i386").

EDIT: According to the [man page]("http://www.die.net/doc/linux/man/man1/byzanz-record.1.html"), it's a command-line application, unless you use the panel applet, that may well be called byzanz-applet.

---

