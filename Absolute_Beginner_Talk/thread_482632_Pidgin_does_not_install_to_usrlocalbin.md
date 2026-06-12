---
title: "Pidgin does not install to usr/local/bin"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Jexel on 2007-06-23
I've installed all the dependences, ran ./configure, ran make, ran sudo make install however it installs to the directory where I extracted the pidgin source code to rather than usr/local/bin so it doesn't appear in the applications list.

What am I doing wrong?

Also, after i've installed pidgin correctly, would it overwrite gaim or do i have to uninstall gaim manually?

Thanks a lot for the help!

---

### Post by Happy_Man on 2007-06-23
Instead of manually compiling, I highly suggest the use of the .debs from [http://getdebs.net](http://getdebs.net). Much more painless. 

You would, I believe, have to uninstall GAIM manually. Although, it won't do anything to hurt Pidgin by staying....

---

### Post by Jexel on 2007-06-23
hmm yes I've been told that by another member. However, this is part of the learning experience so might as well get my hands dirty in the beginning. :)

---

### Post by Happy_Man on 2007-06-23
Not to seem mean, but as I always say....

"If you're that enthusiastic about compiling, get Gentoo. You will compile everything, and if one single letter is off, it'll blow up and you'll have to start over again. No pressure, though."

---

### Post by Jexel on 2007-06-23
Well basically, i just wanna know how to install an application by compiling it. Once I know the basic concepts of how it works and what i need to do, I can start using .debs. Also in the future I may be forced to compile an application, so knowledge of basic compilation is always good.

---

### Post by Malibu Illusion on 2007-06-23
Using packaged files is recommended, but not always practical if you wish to stay up to date with things immediately or whatever you're trying to install has no packaged files for Ubuntu.

Pidgin, by default, should install to the /usr/local/bin directory.  Try this to be sure:

```
./configure --prefix=/usr/local
make
sudo make install
```

This should install the libpurple libraries to /usr/local/lib and the binary to /usr/local/bin.

---

### Post by Jexel on 2007-06-23
that seems to have worked except pidgin doesn't appear in the applications list :(

---

### Post by Happy_Man on 2007-06-23
Try refreshing the panels by entering this into a terminal:
```
killall gnome-panel
```

---

### Post by Jexel on 2007-06-23
legend!

thanks a lot for ALL your help. Greatly appreciated!!!

---

### Post by logos34 on 2007-06-23
nevermind, you resolved your prob.

---

### Post by Malibu Illusion on 2007-06-23
No problem.  Kudos for trying yourself first and telling us exactly what you had tried in your question.  Well worded.

Take care.

---

