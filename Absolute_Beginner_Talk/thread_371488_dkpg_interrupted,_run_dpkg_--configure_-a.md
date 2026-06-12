---
title: "dkpg interrupted, run dpkg --configure -a"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by tomculb on 2007-02-27
I got a message something like the above when trying to add a new program.  I copied the command into Terminal, held my breath, hit Enter and got this, which means nothing to me:

"dpkg: parse error, in file `/var/lib/dpkg/available' near line 7263 package `language-pack-br':
 field name `"

I tried adding a program a second time, and got a dialog box saying something like "not all changes succeeded", an option to look a terminal window, which had what's quoted above but this added:
"E:  Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:"

I've been using this new operating system for about 48 hours now, and I think I'm way over my head on this problem.  Can anyone help me out?

Thanks.

---

### Post by pstep9407 on 2007-02-27
Which package were you trying to install? That helps a lot, because folks can try to replicate what you did. I have been running into similar issues lately. I found some help using Debian's exhaustive [apt-get how-to document]("http://www.debian.org/doc/manuals/apt-howto/"). 

I try ```
apt-get -f install
```, then 

```
dpkg --configure -a
```

This seems to work, but doesn't resolve the problem that causes it. It provides a temprary fix, though, and allows me to use the newly-installed software.

---

