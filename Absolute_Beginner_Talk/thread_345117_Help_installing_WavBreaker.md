---
title: "Help installing WavBreaker"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Icemanyurt on 2007-01-23
I am trying to install WavBreaker and I have big headaches I have no clue what I am doing wrong.

I am using Breezy Badger, the files are located under user/cburk/wavbreaker/wavbreaker-0.7

After running configure (with sh configure), I get the output run 'make; make install'

I run it under using sudo and get the output  
> make  all-recursive
make[1]: Entering directory `/home/cburk/wavbreaker/wavbreaker-0.7'
Making all in src
make[2]: Entering directory `/home/cburk/wavbreaker/wavbreaker-0.7/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cburk/wavbreaker/wavbreaker-0.7/src'
Making all in images
make[2]: Entering directory `/home/cburk/wavbreaker/wavbreaker-0.7/images'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cburk/wavbreaker/wavbreaker-0.7/images'
make[2]: Entering directory `/home/cburk/wavbreaker/wavbreaker-0.7'
make[2]: Leaving directory `/home/cburk/wavbreaker/wavbreaker-0.7'
make[1]: Leaving directory `/home/cburk/wavbreaker/wavbreaker-0.7'
Making install in src
make[1]: Entering directory `/home/cburk/wavbreaker/wavbreaker-0.7/src'
make[2]: Entering directory `/home/cburk/wavbreaker/wavbreaker-0.7/src'
/bin/bash ../mkinstalldirs /usr/local/bin
  /usr/bin/install -c wavbreaker /usr/local/bin/wavbreaker
/usr/bin/install: cannot create regular file `/usr/local/bin/wavbreaker': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/cburk/wavbreaker/wavbreaker-0.7/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/cburk/wavbreaker/wavbreaker-0.7/src'
make: *** [install-recursive] Error 1


Help please

---

### Post by moshuptrail on 2007-01-23
It's acting like you didn't use sudo.
But you said you did.
So, could it be "losing" the sudo somewhere in make?  I couldn't say.

Does /usr/local/bin exist?  What owner and permissions does it have?

---

### Post by Icemanyurt on 2007-01-23
It does exist, and the owner is root

---

