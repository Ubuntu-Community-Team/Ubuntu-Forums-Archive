---
title: "problem running flash application in 6.10"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by moredhel on 2007-02-22
when i try to run a game (called N), done in flash, nothing happens, when run in terminal it says this:

./n_v14: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

it definitely worked on fedora core 5 :\ So does anyone know what's wrong?

the download is here if anyone wants to try or whatever: [http://www.harveycartel.org/metanet/n_v1linux.tar.gz](http://www.harveycartel.org/metanet/n_v1linux.tar.gz)

Thanks in advance

PS: Also, what is copy in bash? I know that paste is shift+insert...

---

### Post by moredhel on 2007-02-23
hmm, i reinstalled libgtk, and now it says:

error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

reinstalling libstdc++ & libc6 doesn't solve this one....

any help?

---

### Post by netkid91 on 2007-02-23
I have never heard about running flash stuff out of a browser under Linux (I have on windows though), what extra packages did you install to get to where you are?

---

### Post by moredhel on 2007-02-23
I don't get what you mean...

all i did was download the linux version of the game, then get to it via terminal then do ./nameofthefile

---

### Post by netkid91 on 2007-02-23
It's not flash BTW, you were really confusing me there!  The C++ libraries included with Ubuntu are newer than the game is looking for, install libstdc++2.10-glibc2.2 over APT or synaptic and it'll work.
Edit: It's in the universe Repo BTW, so turn that on

---

### Post by moredhel on 2007-02-24
thanks, that worked :) :) :)

(BTW, it is flash, i promise, though it isn't a .swf)

---

### Post by netkid91 on 2007-02-26
Well, either way it worked, and your welcome.  If you ever need anything else, don't be afraid to ask, that's why I'm here.

---

