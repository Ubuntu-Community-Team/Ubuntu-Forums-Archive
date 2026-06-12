---
title: "uninstall hamachi"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by dstomov on 2007-11-09
hi,
I have server edt upgraded to 7.10 and i put on it hamachi, but it changed something an now my ip is not 192.168.0.xx, but 5.165.124.xxx and my server is not seen in the local net, of course hamachi is not working :confused:. now i don't want hamachi, but please help me to uninstall it, because there is not uninstall script in the install file.
10x

---

### Post by dstomov on 2007-11-09
:) i found why my address is not 192.168.0.xx, and fix it, by hamachi is still not working and i want to remove it, is it enough to delete its files :-k

---

### Post by Raymond Day on 2008-01-11
I upgraded Ubuntu server and hamachi stopped working too.

Just typing it's name on the command line comes back with nothing.

hamachi list

show nothing. I guess have to uninsall and install it.

I did make clean but it don't work.

I did a reinstall to but that did not work. I guess have to uninstall it 1st.

But I don't know how.

-Raymond Day

---

### Post by zoopzoop on 2008-03-20
Bump!

Same question: how to uninstall Hamachi?
I accidentally installed the wrong version (the pentium version).

I installed it by running "make install" and this is the content of the Makefile:

```

#
#       Where hamachi and its symbolic link hamachi-init goes
#
HAMACHI_DST ?= /usr/bin

#
#       Where root-level tunnel device configuration daemon tuncfg goes
#
TUNCFG_DST  ?= /sbin

.phony: install

install:

        @echo
        @echo Copying hamachi into $(HAMACHI_DST) ..
        @install -m 755 hamachi $(HAMACHI_DST)

        @echo Creating hamachi-init symlink ..
        @ln -sf $(HAMACHI_DST)/hamachi $(HAMACHI_DST)/hamachi-init

        @if which gcc > /dev/null 2>&1; then \
                echo "Compiling tuncfg .."; \
                make -sC tuncfg; \
        fi;

        @echo Copying tuncfg into $(TUNCFG_DST) ..
        @install -s -m 700 tuncfg/tuncfg $(TUNCFG_DST)

        @echo
        @echo "Hamachi is installed. See README for what to do next." 

```

Is it enough to delete hamachi and hamachi-init from /usr/bin and tuncfg from /sbin?
Or did the install set up something else somewhere?
Help please!

---

### Post by Oldsoldier2003 on 2008-03-20
> **zoopzoop said:**
> Bump!

Same question: how to uninstall Hamachi?
I accidentally installed the wrong version (the pentium version).

I installed it by running "make install" and this is the content of the Makefile:

```

#
#       Where hamachi and its symbolic link hamachi-init goes
#
HAMACHI_DST ?= /usr/bin

#
#       Where root-level tunnel device configuration daemon tuncfg goes
#
TUNCFG_DST  ?= /sbin

.phony: install

install:

        @echo
        @echo Copying hamachi into $(HAMACHI_DST) ..
        @install -m 755 hamachi $(HAMACHI_DST)

        @echo Creating hamachi-init symlink ..
        @ln -sf $(HAMACHI_DST)/hamachi $(HAMACHI_DST)/hamachi-init

        @if which gcc > /dev/null 2>&1; then \
                echo "Compiling tuncfg .."; \
                make -sC tuncfg; \
        fi;

        @echo Copying tuncfg into $(TUNCFG_DST) ..
        @install -s -m 700 tuncfg/tuncfg $(TUNCFG_DST)

        @echo
        @echo "Hamachi is installed. See README for what to do next." 

```

Is it enough to delete hamachi and hamachi-init from /usr/bin and tuncfg from /sbin?
Or did the install set up something else somewhere?
Help please!

```
sudo apt-get purge hamachi
```

---

### Post by zoopzoop on 2008-03-20
It says "Couldn't find package hamachi", which I think is logical because I didn't install it using apt-get.

---

### Post by drdos2006 on 2008-03-21
Use "Places" -> "Search" -> "Search for Files" to look for hamachi in the Files System.

A header file is in the /usr/src and hamachi.ko is found in /lib/modules.

From a terminal type "sudo rm /pathname/hamachi file to remove the files.

regards

---

### Post by zoopzoop on 2008-03-22
Thanks for your response, drdos2006.
I removed the two files you mentioned and the tuncfg directory /sbin/tuncfg (I wanted to make sure that I get the tuncfg that is included in the other version, in case that one is different).
Then I installed the new version and everything worked fine!

---

