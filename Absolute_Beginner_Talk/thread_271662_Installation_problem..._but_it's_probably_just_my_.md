---
title: "Installation problem... but it's probably just my fault."
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by mon_m on 2006-10-05
Hey, I'm just trying to see if I can get boo running on ubuntu, but, of course, I'm having some issues.

```

wget http://dist.codehaus.org/boo/distributions/boo-0.7.6.2234.tar.gz
tar xzvf boo-0.7.6.2234.tar.gz
cd boo-0.7.6.2234
./configure --prefix=/usr/local
make
sudo make install
```

I was almost positive that's all I would have to do, but apparently, 'make' is an unrecognized command in my console...  Is there something wrong, or was this switched up on me?

Anyways, any help at all would be appreciated, thank you.

---

### Post by Tamil on 2006-10-05
Try after running this

```
sudo aptitude install build-essential
```

---

### Post by anaconda on 2006-10-05
The c-compiler isn't included to the basic install of ubuntu.

go to synaptic packkage manager, and install them.
Sorry cant remember exactly, but you need atleast 
gcc

EDIT someone beat me to it, with a better hint..
Build essential includes gcc

---

### Post by mon_m on 2006-10-05
Awesome.  Well, that definately solved the whole 'unknown command' issue.  Thank you.  Out of curiosity, why isn't that package pre-installed with Ubuntu?

Anyways, I've run into another problem now - not sure if this is something I can get help with, but here goes:

```

admin@mon-mob:~/boo-0.7.6.2234$ make
Making all in bin
make[1]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
Making all in extras
make[1]: Entering directory `/home/admin/boo-0.7.6.2234/extras'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234/extras'
make[1]: Entering directory `/home/admin/boo-0.7.6.2234'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234'
admin@mon-mob:~/boo-0.7.6.2234$ sudo make install
Making install in bin
make[1]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
make[2]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/boo" || mkdir -p -- "/usr/local/lib/boo"
 /usr/bin/install -c -m 644 'booc.exe' '/usr/local/lib/boo/booc.exe'
 /usr/bin/install -c -m 644 'booi.exe' '/usr/local/lib/boo/booi.exe'
 /usr/bin/install -c -m 644 'booish.exe' '/usr/local/lib/boo/booish.exe'
 /usr/bin/install -c -m 644 'booc.rsp' '/usr/local/lib/boo/booc.rsp'
 /usr/bin/install -c -m 644 'booc.exe.config' '/usr/local/lib/boo/booc.exe.config'
 /usr/bin/install -c -m 644 'booi.exe.config' '/usr/local/lib/boo/booi.exe.config'
 /usr/bin/install -c -m 644 'booish.exe.config' '/usr/local/lib/boo/booish.exe.config'
make  install-data-hook
make[3]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
for lib in Boo.Lang.dll Boo.Lang.Useful.dll Boo.Lang.Compiler.dll Boo.Lang.Parser.dll Boo.Lang.Interpreter.dll Boo.Lang.CodeDom.dll; do                        \                echo "no /i ${lib} /package boo /gacdir //usr/local/lib" ;     \                no /i ${lib} /package boo /gacdir //usr/local/lib || exit 1 ;  \        done
no /i Boo.Lang.dll /package boo /gacdir //usr/local/lib
/bin/sh: line 2: no: command not found
make[3]: *** [install-data-hook] Error 1
make[3]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
make: *** [install-recursive] Error 1
admin@mon-mob:~/boo-0.7.6.2234$ sudo make Making all in bin
make[1]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
Making all in extras
make[1]: Entering directory `/home/admin/boo-0.7.6.2234/extras'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234/extras'
make[1]: Entering directory `/home/admin/boo-0.7.6.2234'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234'
admin@mon-mob:~/boo-0.7.6.2234$ sudo make install
Making install in bin
make[1]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
make[2]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/boo" || mkdir -p -- "/usr/local/lib/boo"
 /usr/bin/install -c -m 644 'booc.exe' '/usr/local/lib/boo/booc.exe'
 /usr/bin/install -c -m 644 'booi.exe' '/usr/local/lib/boo/booi.exe'
 /usr/bin/install -c -m 644 'booish.exe' '/usr/local/lib/boo/booish.exe'
 /usr/bin/install -c -m 644 'booc.rsp' '/usr/local/lib/boo/booc.rsp'
 /usr/bin/install -c -m 644 'booc.exe.config' '/usr/local/lib/boo/booc.exe.config'
 /usr/bin/install -c -m 644 'booi.exe.config' '/usr/local/lib/boo/booi.exe.config'
 /usr/bin/install -c -m 644 'booish.exe.config' '/usr/local/lib/boo/booish.exe.config'
make  install-data-hook
make[3]: Entering directory `/home/admin/boo-0.7.6.2234/bin'
for lib in Boo.Lang.dll Boo.Lang.Useful.dll Boo.Lang.Compiler.dll Boo.Lang.Parser.dll Boo.Lang.Interpreter.dll Boo.Lang.CodeDom.dll; do                        \                echo "no /i ${lib} /package boo /gacdir //usr/local/lib" ;     \                no /i ${lib} /package boo /gacdir //usr/local/lib || exit 1 ;  \        done
no /i Boo.Lang.dll /package boo /gacdir //usr/local/lib
/bin/sh: line 2: no: command not found
make[3]: *** [install-data-hook] Error 1
make[3]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/admin/boo-0.7.6.2234/bin'
make: *** [install-recursive] Error 1

```

Not too sure what's going on. ](*,)

---

### Post by petri on 2006-10-05
Because Ubuntu is for new people in Linux the most of the programs can be installed with **Synaptic**, that may be the reason why build-essential isn't a standard. :) 

I found **boo** in Synaptic. You may have to activate universe and multiverse to find it. :mrgreen:

---

### Post by mon_m on 2006-10-05
Hey, wow, well that definately makes it a lot easier...

I didn't realize synaptic would include something as obscure as that, so I guess I wasted some time trying to do it the hard way.  But anyways, thanks for the help from everyone.

---

