---
title: "Please help with rtlinux or rtai"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by wjhildreth on 2007-05-31
Hello all,

Can you please help me?

I want to compile EMC2 under Feisty Fawn. I need either rtlinux or rtai to be able to run my cnc router with this software.

I have tried installing both rtlinux and rtai using the Synaptic Package Manager. But either way I get the following error run i run 

sudo ./configure

from the src directory

> joeh@joeh-ubuntu:~/downloads/emc2/src$ sudo ./configure
checking installation prefix... /usr/local
checking for RT dir... configure: error: RT not found.  Specify:
        --with-realtime=<path>
or use
        --enable-simulator
to build without a realtime system.
joeh@joeh-ubuntu:~/downloads/emc2/src$ 


First I tried with rtlinux. When it failed I removed it with the package manager but it gave me the error that it was never installed. Funny, I went through the install process and had to read a Lic. agreement for the docs and they did install.

Can someone explain how to install either of these two things to help me along with my project?

For those interested you can find EMC2 at the following URL

[http://www.linuxcnc.org/]("http://www.linuxcnc.org/")

Many thanks.

Joe Hildreth

---

