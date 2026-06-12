---
title: "dpkg help"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Vitaminc23456 on 2007-04-02
So im having a little bit of trouble with the 2nd part of the "13 things you should do after installing ubuntu to your computer" [http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)
Basically it was telling me that:

**"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."**

Well i tried to dpkg config and that told me that i needed to be a superuser to do that. 

so i looked up this problem on the forums and saw someone told someone else to run:
[B]
$ sudo dpkg - - configure -a[/B]

and it brought up a bunch of options, but never changed anything.

sooooooo whats wrong? and im not very computer savvy.

---

### Post by Majorix on 2007-04-02
What are the options there? Can you please post them?

---

### Post by Vitaminc23456 on 2007-04-02
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by Vitaminc23456 on 2007-04-02
it also gives me the same message when i try to update.

---

### Post by miggols99 on 2007-04-02
I think you missed out the spaces with it. It should be like this:

```
sudo dpkg --configure -a
```

---

### Post by jvc26 on 2007-04-02
To solve it you need put put the code in like miggols99 said  - basically you just run the exact command that the error told you to with sudo in front in the terminal, and that will fix the issues.
Il

---

### Post by Majorix on 2007-04-02
Ah yes I didn't look closely. There has to be a space between "dpkg" and "--configure". Do not mix it up with "dpkg-reconfigure" which has no space.

Good luck.

---

### Post by Vitaminc23456 on 2007-04-02
well it appears that worked, im an idiot, thanks

---

### Post by adarkmethod on 2007-04-08
iI'm having a similar problem, exceptt, mmine freezes on Sun-java6-bin, verytime I run a package managr, no matter which one it is

---

### Post by jolzee on 2007-04-13
> iI'm having a similar problem, exceptt, mmine freezes on Sun-java6-bin, verytime I run a package managr, no matter which one it is

I was having this problem until I realised that when the package pops up the license agreement you need to scroll all the way to the bottom and tick and agreement check box. If you don't it'll bomb out.

---

