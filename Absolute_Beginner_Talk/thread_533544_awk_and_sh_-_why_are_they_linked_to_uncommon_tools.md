---
title: "awk and sh - why are they linked to uncommon tools"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by dwhitney67 on 2007-08-24
Why do the powers that be (at Ubuntu) feel that they must link /usr/bin/awk to /etc/alternatives/mawk and /bin/sh to /bin/dash?

It's really disconcerting when a simple shell-script such as follows can't perform a basic function:

```
#!/bin/sh

cp file{,.bak}
```

When I first came across this problem a month or so ago, I couldn't figure out what the hell was going on until I found that the issue was with how /bin/sh is setup.  The solution to this problem was to remove the /bin/sh link and then recreate it with a link to /bin/bash.

Tonight a similar issue occurred while attempting to use awk.  I was attempting to build glibc-2.5.1 and the damn things fails when attempting to run some awk commands.  Could the folks at GNU inserted a bug into their Makefiles??  Nope... the problem was troubleshooted to the way /usr/bin/awk is setup.  The solution... I removed the /usr/bin/awk link and then recreated it with a link to /usr/bin/gawk (which I had to apt-get!!).

Ubuntu... it wants to be so different from the rest of the crowd.  Sometimes being different can be nauseating.  Create a link to that!

---

### Post by lloyd_b on 2007-08-24
"sh" is *supposed* to point to a less powerful shell than "bash" - "dash" is written to comply to POSIX standards for a shell, while "bash" says the heck with POSIX and implements all sorts of useful features.

The "sh->dash" link is so that scripts written for a POSIX shell will work correctly.

Now for a simple counter-question:  why did you specify "#!/bin/sh", when you clearly wanted to use "bash"?  It's just as easy to specify "#!/bin/bash"...

I'm not all that familiar with "awk", but I suspect that link is for a similar reason - to provide backwards compatibility to a "standard" version of "awk".

Net result - "bash" and "gawk" are *not* the "Unix standard" versions of those tools.  While pretty much every Linux variant has them, when you start looking at other Unix variants (AIX, Solaris, etc) things are much different.  The maintainers of Linux distro's are aware of this, and try to keep Unix standard commands (like "sh" and "awk") pointed toward the less capable but more universal version of those tools.

Lloyd B.

---

