---
title: "inter-dependent dependencies for build-essential"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-10
I am trying to install build-essential manually after downloading the deb files. But the following dependencies depend on each other:

libstdc++6-4.0-dev_4.0.1-4ubuntu9-i386.deb
g++-4.0.1-3_i386.deb

As a result, I cannot install either of them. And by implication, build-essential.

Any ideas?

---

### Post by Sutekh on 2006-03-10
Compiling source code?  build-essential is on the installation CD (which hopefully you have)

Use this command to ensure the CD is a local repository
```
sudo apt-cdrom add
```
Then install build-essential off the CD
```
sudo apt-get install build-essential
```

---

### Post by engla on 2006-03-10
This might be dumb, sorry for that, but have you tried putting both in the same command?

sudo dpkg -i pkg1.deb pkg2.deb
[where pk1 and pk2 are the long names above :]

---

### Post by AtinLango on 2006-03-10
[QUOTE=engla]This might be dumb, sorry for that, but have you tried putting both in the same command?

sudo dpkg -i pkg1.deb pkg2.deb
[where pk1 and pk2 are the long names above :][/QUOTE]

That was not dumb at all. It works!!

And Sutekh's suggestion is great too. It works as well only that it found an up-to date build-install already. Anyway, I am wondering why build-essential was not installed by default.

---

### Post by Sutekh on 2006-03-10
[QUOTE=AtinLango]That was not dumb at all. It works!!

And Sutekh's suggestion is great too. It works as well only that it found an up-to date build-install already. Anyway, I am wondering why build-essential was not installed by default.[/QUOTE]
A much asked question.  I can only assume that it's put on the CD for those who need it, but not installed as a large proportion of people may never actually compile source code.  Save some space and all.

---

### Post by AtinLango on 2006-03-10
[QUOTE=Sutekh]A much asked question.  I can only assume that it's put on the CD for those who need it, but not installed as a large proportion of people may never actually compile source code.  Save some space and all.[/QUOTE]

I think thats right. I couldn't agree more.

---

