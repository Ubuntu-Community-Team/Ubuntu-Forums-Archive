---
title: "tarballs"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by gabz8472 on 2007-08-10
sorry, i've been trying to install software and most of wht i've found are .tar.bz2 files. I've followed all the directions I could find on installing them but no good.

I can run the ./compile command and it works ok, but when i try the 'make' command, it gives me this error message:
make : *** No targets specified and no makefile found.  Stop.

I saw in an earlier thread a similar problem and he was asked  to post the last few lines of the ./cofigure command

this is mine:

Alternatively, you may set the environment variables VFS_CFLAGS and VFS_LIBS to avoid the need to call pckg-config.

I am trying to install synce to synce this laptop to my ppc device. Please help.

---

### Post by skymera on 2007-08-10
ok thats wheree i give up too.
i do the ./configure etc
then make and same error!

hopefully someone with knowledge can help

---

### Post by BaffledMollusc on 2007-08-10
You probably both know this, but I'll point it out just in case.

If you use the package manager you can install tens of thousands (particularly if you enable the "multiverse" repositories) of applications with a simple click of the mouse. You don't need to play around with tarballs and compiling your own app.

Look under Applications->Add/Remove or System->Administration->Package Manager.

---

### Post by hyper_ch on 2007-08-10
What are you trying to install? Are you sure it's no in the repositoires?

And for compiling etc you need some additional software:
```

sudo apt-get install build-essentials

```

---

### Post by skymera on 2007-08-10
someitmes its in Repos.

but sometimes on unknown packages you compile..
rather than a Deb file.

---

