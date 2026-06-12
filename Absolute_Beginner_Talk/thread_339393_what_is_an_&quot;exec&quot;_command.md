---
title: "what is an &quot;exec&quot; command?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by hopestorm on 2007-01-15
I want to install my matlab on linux.

The installation shell reads:

#! /bin/sh 
dirs=`dirname $0`
args=$@
exec $dirs/unix/install -nocp $args 

when I run this shell, I got the message (root the same):

bash: /cdrom/install_unix.sh: /bin/sh: bad interpreter: Permission denied

I am not sure whether this is because "exec" not recognized in ubuntu.
I use which and can't find "exec" though.

---

### Post by oyvindaa on 2007-01-15
exec is for executing something .. i.e starting or stopping a program.

I'm not a programmer but I believe that's what it does.

---

