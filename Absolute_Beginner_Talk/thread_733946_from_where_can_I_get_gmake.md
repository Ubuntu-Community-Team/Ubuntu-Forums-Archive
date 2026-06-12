---
title: "from where can I get gmake?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by mizuiro on 2008-03-24
Hi,

   From where can I get gmake? I have already done "sudo apt-get install build-essential". After reading some posts,  I dit "sudo ln -s /usr/bin/make /usr/bin/gmake", but 
***  ln: accessing '/usr/bin/gmake': Not a directory *** is found. 

   And when I type "make",  make: *** No targets specified and no makefile found. Stop. 
But there is Makefile.am and Makefile.in in the current directory.

  When I type "gmake",  bash: gmake: command not found occurred.

Any help would be much appreciated!

thanks in advance,
mizu

---

### Post by Diabolis on 2008-03-24
sudo apt-get install make? have you tried it?

also before you can "make", you have to configure with "./configure" so the make file is created correctly.

---

### Post by mikeyphi on 2008-03-24
In Ubuntu you just use "make" 
NOT "gmake"

What exactly are you doing?

---

