---
title: "i am getting a weird error when installing wine"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by Muk on 2005-07-15
yes i do not know how to solve this on ubuntu

-------------------------------------------------------------------------------------
jack@muk:/wine-20050628/tools$ sh wineinstall
WINE Installer v0.74

/wine-20050628 /wine-20050628/tools
Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Configure failed, aborting install.
------------------------------------------------------------------------------------------------ ](*,) 
 :| 
that is the error i am getting and i dont know how to solve it. Please help

---

### Post by odin on 2005-07-15
Why dont you try with synaptics or apt to do that? It's much easier

---

### Post by doclivingston on 2005-07-15
The easiest way of getting everything you need to be able to compile stuff is to install the package "build-essential" (i.e. via synaptic, or `sudo apt-get install build-essential`).

---

