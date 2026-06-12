---
title: "installing libx11 problem"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by nanxy85 on 2008-03-05
E: Couldn't find package xlibs-dbg


i got the above error when i try to install libx11
code that i type is:
apt-get install libx11-6 libx11-dev libxt6 libxt6-dbg libxext6 libxtst-dev libxtst6 xlibs-dbg xlibs-dev

---

### Post by oedha on 2008-03-05
means......xlibs-dbg was not on the (ubuntu)repository.......
and that package also not available in [http://packages.ubuntu.com](http://packages.ubuntu.com)
but
you can get it from [http://packages.debian.org/sarge/xlibs-dbg](http://packages.debian.org/sarge/xlibs-dbg)

---

### Post by nanxy85 on 2008-03-05
when i type 
apt-get -f install libx11-6 libx11-dev libxt6 libxt6-dbg libxext6 libxtst-dev libxtst6 xlibs-dbg xlibs-dev


Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-6 is already the newest version.
libxt6 is already the newest version.
libxext6 is already the newest version.
libxtst6 is already the newest version.
xlibs-dbg is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libx11-dev: Depends: libx11-6 (= 2:1.0.0-0ubuntu9.1) but 2:1.1.1-1ubuntu4 is to be installed
              Depends: x11proto-core-dev (>= 6.8.99.8-1) but it is not going to be installed
              Depends: x11proto-kb-dev but it is not going to be installed
              Depends: x11proto-input-dev but it is not going to be installed
              Depends: libxau-dev but it is not going to be installed
              Depends: libxdmcp-dev but it is not going to be installed
              Depends: x11proto-kb-dev but it is not going to be installed
  libxt6-dbg: Depends: libxt6 (= 1:1.0.0-0ubuntu3) but 1:1.0.5-3 is to be installed
  libxtst-dev: Depends: libxtst6 (= 2:1.0.1-0ubuntu2) but 2:1.0.2-1ubuntu1 is to be installed
               Depends: libxext-dev but it is not going to be installed
               Depends: x11proto-record-dev but it is not going to be installed
  xlibs-dbg: Depends: libice6-dbg but it is not going to be installed
             Depends: libsm6-dbg but it is not going to be installed
             Depends: libx11-6-dbg but it is not going to be installed
             Depends: libxext6-dbg but it is not going to be installed
             Depends: libxft1-dbg but it is not installable
             Depends: libxi6-dbg but it is not going to be installed
             Depends: libxmu6-dbg but it is not going to be installed
             Depends: libxmuu1-dbg but it is not going to be installed
             Depends: libxp6-dbg but it is not going to be installed
             Depends: libxpm4-dbg but it is not going to be installed
             Depends: libxrandr2-dbg but it is not going to be installed
             Depends: libxtrap6-dbg but it is not going to be installed
             Depends: libxtst6-dbg but it is not going to be installed
  xlibs-dev: Depends: libice-dev but it is not going to be installed
             Depends: libsm-dev but it is not going to be installed
             Depends: libxext-dev but it is not going to be installed
             Depends: libxi-dev but it is not going to be installed
             Depends: libxmu-dev but it is not going to be installed
             Depends: libxmuu-dev but it is not going to be installed
             Depends: libxpm-dev but it is not going to be installed
             Depends: libxrandr-dev but it is not going to be installed
             Depends: libxt-dev but it is not going to be installed
             Depends: libxtrap-dev but it is not going to be installed
             Depends: libxv-dev but it is not going to be installed
             Depends: x-dev but it is not going to be installed
             Depends: zlib1g-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


help...............................................

---

### Post by oedha on 2008-03-05
> **nanxy85 said:**
> when i type 
apt-get -f install libx11-6 libx11-dev libxt6 libxt6-dbg libxext6 libxtst-dev libxtst6 xlibs-dbg xlibs-dev

from terminal
sudo apt-get update
then
what if :==> sudo apt-get install libx11-6......bla...bla...bla

---

### Post by nanxy85 on 2008-03-05
how can i include the [http://packages.debian.org/sarge/xlibs-dbg](http://packages.debian.org/sarge/xlibs-dbg) in repositories?

deb [http://packages.debian.org/sarge/xlibs-dbg](http://packages.debian.org/sarge/xlibs-dbg) ....   ???...... then what?

thank you

---

### Post by zvacet on 2008-03-05
Which version of Ubuntu do you runing,and did you try to install package with synaptic?Do you have all repos open?

---

### Post by nanxy85 on 2008-03-05
i think i have problem with the repositories or the sources.list  coz some of the dependencies for libx11 not found... like 
x11proto-core-dev,
x11proto-kb-dev,
x11proto-input-dev,
libxau-dev,
libxdmcp-dev,
x11proto-kb-dev

how can i get this? obviously, apt-get cannot help.....so any other alternative?
i been stuck with this problem for how many week oredi.....help needed.....

---

### Post by nanxy85 on 2008-03-05
Ubuntu 7.10 the Gutsy Gibbon. There is no such file as i mention above in the repositories. yes there are libx11 but not the dependencies. That's why i need the sources.list.....in case i already mess up mine without realizing it....plz dont ask me to check the repositories again...if there is such file i would have seen it.....i need the sources.list that point to all the complete package for libx11....if there is none then plz point me to the right step to do it one by one.......i dont mind do the long way......just plz help.

---

### Post by zvacet on 2008-03-05
Go to the synaptic and in search box type** libx11** and when you find it install it.It should pull all dependencies with package.You also need** libx11-dev.**

---

