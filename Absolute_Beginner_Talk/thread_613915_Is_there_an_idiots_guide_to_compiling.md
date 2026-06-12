---
title: "Is there an idiots guide to compiling"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-11-15
I want to compile code::blocks for linux, but like most things that need compiling the default make / automake doesnt sem to work. I think i need to understand exactly the steps and processes that are needed in order to understand the always vague cryptic instructions that come with the src. What files are needed to 'make' something and what do they do.

---

### Post by Dr Small on 2007-11-15
You first need to have build-essential if you do not have it.
```
sudo apt-get install build-essential
```

---

### Post by Paul820 on 2007-11-15
There is usually a package already compiled by someone else on [http://forums.codeblocks.org/]("http://forums.codeblocks.org/") in the nightly builds section. If you have a 64bit ubuntu system you can get precompiled packages from here [http://www.esnips.com/web/CodeBlocks]("http://www.esnips.com/web/CodeBlocks")
You can get instructions for building from the codeblocks wiki [http://wiki.codeblocks.org]("http://www.wiki.codeblocks.org")
And if you are compiling the newer version it uses the new wxwidgets2.8 available from the repositories.

---

### Post by Hospadar on 2007-11-15
most build problems are related to dependancy issues, so be very sure you have all the dependancies you need.  99% of the stuff you might need to compile has dependancies that can be found in the repositories, so tracking them down is just a matter of installing the correct *-dev packages from synaptic.

Have a close look at the dependancy list for the stuff you are building, and search for them in synaptic, many will be named like: lib<whatever> and lib<whatever>-dev

---

