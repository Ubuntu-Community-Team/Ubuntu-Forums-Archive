---
title: "Kismet"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by Nirva on 2006-11-04
Hay,

I am trying to install Kismet on Dapper Drake, so I first downloaded this file : [http://www.kismetwireless.net/code/kismet-2006-04-R1.tar.gz](http://www.kismetwireless.net/code/kismet-2006-04-R1.tar.gz)
I compiled it by executing ./configure

After compiling he says : 

Configuration complete.  Run 'make dep' to generate dependencies
and 'make' followed by 'make install' to compile and install.

filip@Filip:~/Desktop/kismet-2006-04-R1$ make dep
make[1]: Entering directory `/home/filip/Desktop/kismet-2006-04-R1'
make[2]: Entering directory `/home/filip/Desktop/kismet-2006-04-R1'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/filip/Desktop/kismet-2006-04-R1'
make[1]: Leaving directory `/home/filip/Desktop/kismet-2006-04-R1'

So far so good ( I hope ) 

filip@Filip:~/Desktop/kismet-2006-04-R1$ make
make: Nothing to be done for `all'.
filip@Filip:~/Desktop/kismet-2006-04-R1$ make install
make -e commoninstall
make[1]: Entering directory `/home/filip/Desktop/kismet-2006-04-R1'
mkdir -p /usr/local/etc
mkdir -p /usr/local/bin
install -o "root" -g "root" -m 755 scripts/kismet /usr/local/bin/kismet
install: cannot remove `/usr/local/bin/kismet': Permission denied
make[1]: *** [commoninstall] Error 1
make[1]: Leaving directory `/home/filip/Desktop/kismet-2006-04-R1'
make: *** [install] Error 2
filip@Filip:~/Desktop/kismet-2006-04-R1$ make suidinstall
make -e commoninstall
make[1]: Entering directory `/home/filip/Desktop/kismet-2006-04-R1'
mkdir -p /usr/local/etc
mkdir -p /usr/local/bin
install -o "root" -g "root" -m 755 scripts/kismet /usr/local/bin/kismet
install: cannot remove `/usr/local/bin/kismet': Permission denied
make[1]: *** [commoninstall] Error 1
make[1]: Leaving directory `/home/filip/Desktop/kismet-2006-04-R1'
make: *** [suidinstall] Error 2


Does anyone knows what I should do?  When you try to explain something, please keep in mind that I know only very very little about Linux

Thanks

---

### Post by podunk on 2006-11-04
Hey! :) Kismet is in the repositories, you can use the Synaptic Package manager for that. No need to compile and install unless you just want to. You may need to enable the extra repositories. This page has good info on that:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

If you want to compile and install just to learn how try giving this page a read:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

