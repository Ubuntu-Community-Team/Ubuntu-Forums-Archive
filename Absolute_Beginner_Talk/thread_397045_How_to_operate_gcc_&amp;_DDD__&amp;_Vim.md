---
title: "How to operate gcc &amp; DDD  &amp; Vim"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by gil michael on 2007-03-30
Hi,

I am a new user. I want to use Ubuntu to compile c programs, I know the compiler is called gcc and the debuger is DDD. Do i have to download these or i've already got them when i installed Ubuntu?
Where can i find those programs?

another q: where can i find a guide to Vim? the text file editor?

Regards,

Gil

---

### Post by lloyd_b on 2007-03-30
To install gcc, run "sudo apt-get build-essential" in a terminal window (or install that package from Synaptic or the Update Manager). 

The "standard" debugger on Linux systems is "gdb".  "DDD" is a graphical front-end for gdb, which makes it easier to use.  I think "gdb" is part of "build-essential", but I doubt it DDD is.

As for a guide to "vim" - start up the editor, and type ":help" - this will bring up some very good documentation for vim.

Lloyd B.

---

