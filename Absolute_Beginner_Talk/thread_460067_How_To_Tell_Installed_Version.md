---
title: "How To Tell Installed Version?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Frederick J. Harris on 2007-05-31
This is going to seem like an incredibly dumb question.  Here goes.  Once you have Xubuntu installed, how can you confirm the version that was installed?  I obtained my Ubuntu/Xubuntu operating systems from the purchase of a book which included a double sided DVD with all the 6.06 (Dapper Drake) distros on one side and the 6.1 (Edgy Eft) distros on the other.  On my first install of Xubuntu it was my intention to install the 6.1 version.  However, I accedentially clicked on the globe in the title bar for Firefox and the welcome screen said "Welcome to Xubuntu 6.06".  When that happened I figured I must have accidently copied the distro from the wrong side of the DVD.  So then I did my second install being very, very careful to make absolutely sure I used...

xubuntu-6.1-desktop-i386.iso

However, when I clicked on Firefox again I'm still getting "Welcome to Xubuntu 6.06"!  Also, I don't have an internet connection so to install software I download .deb files and double click on them or use dpkg and I'm having trouble getting my compilers set up.  I'm beginning to wonder if the book manufacturer made some kind of mistake in creating the DVD and I have 6.06 on both sides?  In Windows it is easy to check what version of Windows you have, how do you do it with Xubuntu???   Thanks!

---

### Post by pbw on 2007-05-31
You can check lots of ways, in terminal cat /etc/apt/sources.list | grep main, see if the word dapper or edgy is displayed.

-- pbw

---

### Post by apunc1 on 2007-05-31
enter in terminal

```
cat /etc/issue
```

---

### Post by drs305 on 2007-05-31
```
lsb_release -a
```

Neither this nor above posts give you the kernel number. You'd get that with:
```
uname -a
```

---

