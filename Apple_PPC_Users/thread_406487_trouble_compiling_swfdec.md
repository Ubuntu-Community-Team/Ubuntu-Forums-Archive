---
title: "trouble compiling swfdec"
date: 2007-04-11
forum: Apple PPC Users
---

### Post by discoandy on 2007-04-11
I've been gleaning great information from the PPC forums!  It seems as we are a small but strong group of people.  I want to help more and add to the dialogue, so consider this my introduction.

I am still pretty new to linux, and trying to compile swfdec it kept telling me:

 error: cannot find pangocairo, which is required for build

there was one before that but I installed the package hoping that my problem would be solved... but there seems to be many requirements I don't have.

is there a way to get all the dependencies for a package easily?

---

### Post by ZoiaGuyver on 2007-04-11
Tbh normally apt/synaptic takes care of the dependencies (although i have hit the same thing with missing ones and also a few that were needed to be older than i had).

I dont know of an easy way to list the dependencies i normally just try it and wait for the errors and use "aptitude search" to find the missing ones :p

---

### Post by Auria on 2007-04-11
also dont forget to install the -dev packages (e.g. dont install just cairo, also install cairo-dev

if it requires version more recent than those from the repos, youll have to build from them source too though

---

### Post by anders_gud on 2007-04-12
> **discoandy said:**
> 
is there a way to get all the dependencies for a package easily?

sudo apt-get build-dep libswfdec0.3

...and probably a recent ffmpeg

Swfdec-mozilla works ok on youtube, but it's unstable (lots of firefox crashes, even xorg...)
I bet Gnash will do a better job in a few weeks...

---

