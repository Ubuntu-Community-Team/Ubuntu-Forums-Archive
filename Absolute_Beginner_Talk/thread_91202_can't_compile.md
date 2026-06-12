---
title: "can't compile"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by ralph4100 on 2005-11-16
tried to compile the gftp source and got:

```
root@ubuntu:/opt/gftp-2.0.18# ./configure make
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/sh ./config.sub make failed
```

So I guess I haven't installed a compiler yet?

How would i do that?

---

### Post by apjone on 2005-11-16
sudo apt-get install automake

sudo apt-get install make

sudo apt-get install makedev

---

### Post by bonzodog on 2005-11-16
no you haven't used a valid command;
the command is JUST #./configure
after thats done, type #make
then when thats done type #make install

or you could pipe them into each other by doing:

root@ubuntu:/opt/gftp-2.0.18# ./configure && make && make install

incidentally gftp is in the pre-built sources?

try doing an #apt-get install gftp

---

### Post by kruz on 2005-11-16
hey ralph its kruz
i take it u got ur pc up and running last night
i didnt see a response and sounds like it

yes 
sudo apt-get install gtfp

give us some output

---

### Post by ralph4100 on 2005-11-16
hey kruz, yeah it took just playing with different configurations of the partition part of the setup over beers, but I got it to work....

my attempt at installing...

```
root@ubuntu:/opt/gftp-2.0.18# sudo apt-get install gftp
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gftp: Depends: gftp-gtk (= 2.0.18-10) but it is not installable
        Depends: gftp-text (= 2.0.18-10) but it is not going to be installed
E: Broken packages
root@ubuntu:/opt/gftp-2.0.18#
```

---

### Post by ralph4100 on 2005-11-16
I also tried

```

sudo apt-get install automake

sudo apt-get install make

sudo apt-get install makedev
```

and only make seemed to install....

makedev was already installed

---

