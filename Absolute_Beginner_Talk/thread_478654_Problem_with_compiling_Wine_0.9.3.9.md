---
title: "Problem with compiling Wine 0.9.3.9"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by bamesah on 2007-06-19
When i try to compile wine 0.9.3.9, this is what i get:

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

How can i make C compiler create executables??

---

### Post by bamesah on 2007-06-19
any ideas?

---

### Post by cogadh on 2007-06-19
Is there a particular reason you are compiling it? There is a 0.9.39 deb package available from Wine's repository.

---

### Post by bamesah on 2007-06-19
But all what i see is wine 0.9.3.8 i don't see 0.9.3.9 ??

---

### Post by cogadh on 2007-06-19
Go here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Follow the instructions for adding the Wine repositories, you will get 0.9.39.

---

### Post by bamesah on 2007-06-19
ok- updated and now i see it, but just for my info. can u tell me how to compile it

---

### Post by cogadh on 2007-06-19
Nope, sorry, I've never tried to do that myself.

---

### Post by nutz on 2007-06-19
> **cogadh said:**
> Go here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Follow the instructions for adding the Wine repositories, you will get 0.9.39.

+1, Then you can just use synaptic...

---

### Post by WW on 2007-06-19
Usually the error "cannot create executables" means you haven't installed all the packages necessary for compiling C programs.  If you don't already have it, try installing **build-essential**.

---

### Post by rattking on 2007-06-19
take a look at the bottom of config.log and try to find where the error is
or post it for us to look at
you are probably missing a dev package or 2

---

### Post by bamesah on 2007-06-19
> **WW said:**
> Usually the error "cannot create executables" means you haven't installed all the packages necessary for compiling C programs.  If you don't already have it, try installing **build-essential**.

This worked, but it also needed Flex and Bison packages

---

### Post by YokoZar on 2007-06-20
Just do apt-get build-dep wine to get all the needed build depends for compiling wine.

That said, there's no need for a hand compile.  You could also build the *package* from scratch, if you wanted to, like with apt-get --build source wine

---

