---
title: "how do I install from source?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by jjf on 2006-03-19
I'm trying to install tuxpaint from source because the version in the repositories keeps crashing on me.  I'm hoping the next version is more stable.

I followed the guide on Aysiu's blog:

```
tar -xvzf tuxpaint-0.9.15b
cd tuxpaint-0.9.15b
./configure
```

At this point I get the following error:
```
bash: ./configure: No such file or directory
```

Help?

---

### Post by taurus on 2006-03-19
Is there a README or INSTALL in that directory?  What is the output of this command then?
```

ls -la tuxpaint-0/9/15b
(or is it tuxpaint-0.9.15b???)

```

---

### Post by jjf on 2006-03-19
Oops.  Yeah, it's tuxpaint-0.9.15b

Ok, I read the INSTALL.txt, and it says they don't have "autoconf" so there is no ./configure.  But I should be able to just skip that step and run "make" from the shell.  It throws errors, so I guess I don't have some of the dependencies installed.  *sigh*  Gotta hunt those down, I guess.

Thanks.

---

### Post by taurus on 2006-03-19
Maybe you don't have the neccessary files to compile it from source.  So, before you run "make" again, try running this command first from a terminal.
```

sudo apt-get install build-essential

```
And if you still can't build it, tell me where to download it and I will check it out myself for you.  ;)

---

### Post by az on 2006-03-19
[QUOTE=jjf]I'm trying to install tuxpaint from source because the version in the repositories keeps crashing on me.  I'm hoping the next version is more stable.
[/QUOTE]


My daughters use it quite often.  We have no problems with it.

What errors do you get if you launch it from a terminal?  Can you reproduce the problem and make it crash?

---

