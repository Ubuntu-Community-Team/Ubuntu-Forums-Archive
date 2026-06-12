---
title: "How to install auctex from source?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by cseljatib on 2007-11-06
hi there

i know that i can install auctex (for emacs) using 
%sudo apt-get auctex

but this seems to only work for emacs21 and not for emacs22 (see this post [https://stat.ethz.ch/pipermail/ess-help/2007-June/004085.html](https://stat.ethz.ch/pipermail/ess-help/2007-June/004085.html)).

I need to have auctex to be used with emacs22, then i need to install it from source, but i have not idea how to do it, any help?


also, how can i make that emacs21 load one .emacs file and emacs22 load a different .emacs file??

Please, help

---

### Post by TravisA on 2007-11-06
I find the easy way is to get apt-get to get the dependancies needed to do is run this command:
sudo apt-get build-dep auctex

That will get everything you need to build from source.  Then just get the source code and follow their instructions.

---

### Post by cseljatib on 2007-11-06
but how auctex will now that i need it for emacs22 and not emacs21??, can you explain further please?

---

