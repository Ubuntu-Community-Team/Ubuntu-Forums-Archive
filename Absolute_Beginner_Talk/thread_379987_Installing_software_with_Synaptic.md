---
title: "Installing software with Synaptic"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by newbie59 on 2007-03-09
I just used Synaptic to locate and download a package named "debsums", an MD5 sum checker for download verification. I looked in the applications area for the package to use it and couldn't find it. I went in and did a reinstall and still could not locate it in applications, places, or system. 
Can someone tell me where I might find this utility??

---

### Post by n_nous on 2007-03-09
In synaptic, if you right click the package you've just installed and click properties from the popup menu you will see a window. 
In this window there is a tab called installed files. There you can see where your application was installed.

---

### Post by igknighted on 2007-03-09
it is likely a CLI tool.  try, in the terminal, typing "debsums pkgname.deb"

---

### Post by newbie59 on 2007-03-09
Please see a small look at what I found:
/usr/share/man/fr
/usr/share/man/fr/man1
/usr/share/man/fr/man1/debsums.1.gz
/usr/share/man/fr/man8
/usr/share/man/fr/man8/debsums_gen.8.gz

Sorry, but this means nothing to me. I still cannot figure out where the program is located.

and when I went to accessories/Terminal and typed in "debsums pkgname.deb"
i got an "debsums: invalid package name `pkgname.deb' response

---

### Post by igknighted on 2007-03-09
> **newbie59 said:**
> Please see a small look at what I found:
/usr/share/man/fr
/usr/share/man/fr/man1
/usr/share/man/fr/man1/debsums.1.gz
/usr/share/man/fr/man8
/usr/share/man/fr/man8/debsums_gen.8.gz

Sorry, but this means nothing to me. I still cannot figure out where the program is located.

and when I went to accessories/Terminal and typed in "debsums pkgname.deb"
i got an "debsums: invalid package name `pkgname.deb' response

well, it works ;-).  You need to replace pkgname.deb with the file or path to the file you want to check.

EDIT: It's in /usr/bin most likely, but it is just that CLI command.  That is the whole program.

---

### Post by n_nous on 2007-03-09
> and when I went to accessories/Terminal and typed in "debsums pkgname.deb"
i got an "debsums: invalid package name `pkgname.deb' response
well, in my opinion that just means that the application is installed, and you just need to give it a valid package name. 
If it isn't installed it will respond with something like "command not found"

---

### Post by newbie59 on 2007-03-09
Well, thank you for your input.

But I'm gonna have to uninstall it because I don't know how to get to it and there is no use in using up disk space on something I can't find or use.

Is there something I can read that will allow me to understand this more??

---

### Post by igknighted on 2007-03-09
you just did use it though.  what file do you want to check the md5 sum for?  I'll tell you syntax to use

---

### Post by nero_86 on 2007-03-09
For control the MD5 of a generic file there is also the md5sum command. In a terminal type

```
md5sum file_name
```

If the file is big the command need a little time to work.

---

