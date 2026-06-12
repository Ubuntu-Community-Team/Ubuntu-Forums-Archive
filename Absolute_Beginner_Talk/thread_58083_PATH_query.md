---
title: "PATH query"
date: 2005-08-18
forum: Absolute Beginner Talk
---

### Post by m.a.fonseca@gmail.com on 2005-08-18
Hi,

I am a brand new user of Ubuntu (2 days old :) ). I am trying to install teTeX into my machine and I've followed the instructions successfully up to the point where they state:

"Now, make sure to put the newly created binaries into your PATH.
Use something like the following, but replace i686-pc-linux-gnu by your
actual platform directory:
  PATH=/usr/local/teTeX/bin/i686-pc-linux-gnu:$PATH; export PATH
or
  setenv PATH /usr/local/teTeX/bin/i686-pc-linux-gnu:$PATH

and run
  texconfig conf
and check if all the output looks ok and then run
  texconfig

My questions are: 

1) What should I replace  i686-pc-linux-gnu by? What is my platform directory?

2) I've tried different combinations of PATHs. Will that be bad for my system? how do I reset PATH to its original state?

Thanks 

Miguel

---

### Post by xmastree on 2005-08-18
Instructions? Where are you instaling it from?

Why not just use synaptic to install it instead?
Much easier, especially for a beginner.

If you haven't already, look at [this](http://www.ubuntuguide.org) and see about enabling the extra repositories. Then run synaptic, search for tetex, select it and go. :cool:

---

