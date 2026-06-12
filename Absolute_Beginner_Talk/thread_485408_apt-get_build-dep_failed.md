---
title: "apt-get build-dep failed"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Foxmike on 2007-06-26
Hi!  

I would like to compile the latest versions of K3b and Amarok.  To do this, I firstly do an
```
sudo apt-get build-dep amarok
```
and
```
sudo apt-get build-dep k3b
```

For those 2 packages, I get the answer (I'm translating from french...)
```
E: The build dependencies for <package-name> can not be satisfied
```

Is that normal?

Thanks in advance!

---

### Post by p_quarles on 2007-06-26
I just looked at the man apt-get page, and from what I can see the "build-dep" option doesn't compile anything, it just looks for dependencies. If you're trying to compile from source, you can't use a package manager.

---

### Post by Foxmike on 2007-06-26
I know that.  What I actually want is make sure I have all the dependencies installed in order to do the ./configure && make && sudo make install .  I Amarok and k3b are in the repositories, there shouldn't be a problem to get the dependencies, I guess, but it doesn't seems to work...:(

Anyway, if anyone has a cue if this is normal.  Perhaps, I'll make a look to my sources.list to make sure everything is there...

---

### Post by p_quarles on 2007-06-26
Sure, but if the latest versions of Amarok and K3b are not in the repos (which is the only reason you would be trying to compile them from source) then apt won't be able to find their dependencies. 

So: I would guess that the response you got from apt is normal. Attempting the compile chain will give you info about any missing dependencies, though, so just go ahead and do that.

---

### Post by Foxmike on 2007-06-27
OK thanks, I'll try with that and see what it does!:)

---

### Post by syxbit on 2008-03-07
the response given is not accurate

build-dep should still have installed the dependencies. even if they were slightly out of date
i don't understand why it didn't work for you, but build-dep makes compiling much easier

---

