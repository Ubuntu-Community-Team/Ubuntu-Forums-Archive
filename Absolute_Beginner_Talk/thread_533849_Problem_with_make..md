---
title: "Problem with make."
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Shack on 2007-08-24
Hey there. I'm having some problems with my fresh install.

I've copied my sources.list from my "working" ubuntu computer, but when I try to install build-essential and make I get error:

Package XXXXX is not available but is referred to by another package.
This may mean that the package is missing, has been obsoleted or is only available from another source.
E: Package XXXXXX has no installition candidate.

-----------------------------------------------------------

Any help with this one would be apriciated. I've done sudo apt-get update and sudo apt-get install.

---

### Post by Vadi on 2007-08-24
Have you tried installing build-essential via Synaptic?

Just search for it there, it'll be the first package that comes up.

---

### Post by Shack on 2007-08-24
Thanks for reply. I managed to install gcc and make with ubuntu cd inserted but I can't install build-essential. When I try to install build-essential it says:

depends: libc6-dev 
depends: g++

and when I try to install these it says:

with libc6-dev | depents: libc6 (libc6 say already the newest versio).
and g++ need some other packages and this just goes on.

So everytime I try to install some depencie, it has another depencie and my wheel just rolls on :(

What to do.

---

### Post by Vadi on 2007-08-24
Did you accidently remove too many packages? :|

Or, maybe your repositories are messed up... (pure guess here). But try going to applications - add/remove - preferences - third party software - and uncheck all repositories, and try installing build-essential again?

---

### Post by nixclusive on 2007-08-24
you are probably installing using dpkg, try using apt-get; in the terminal enter:```
sudo apt-get install build-essential
```

---

### Post by Shack on 2007-08-24
Thank you again guys.

I've been using apt-get and synaptic package manager, but I have same problem with boths.

It seem like I should install g++ and libc6 these two with all of their depencies, but I run on the wall all the time. I get error that I have to install libc6 which is already installed and all the time I seem to miss some depencies.

---

### Post by punx45 on 2007-08-24
> **Shack said:**
> 
I've copied my sources.list from my "working" ubuntu computer

im going to venture a guess and say that this is the source of your troubles.

---

### Post by schorsch on 2007-08-24
What is the output of
```
dpkg -l | grep libc6
```
... just to make sure which version of libc6 you have installed right now ...

---

