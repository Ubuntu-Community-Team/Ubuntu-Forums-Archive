---
title: "Manual &quot;Installation&quot;"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Mosod on 2008-02-01
Maybe this is more than a beginner question but, while I at least like to think I'm pretty computer savvy,  I've only been using Linux for 2 days and I'm Linux/Unix retarded.

My general question, and really the more important one, is how do I "install" a program if its delivered as a zipped up directory?

My explicit question involves Eclipse 3.3.  I've been using it for some time at work on a windows machine with Cygwin and thought it would be nice to get it up an running on my home computer where I just installed Gutsy.  So I grabbed the latest download from the Eclipse website but I can't for the life of me figure out what to do with it.  I assume I should just unpack it into a directory somewhere but I have no idea what directory that is.  I have no idea how to make a shortcut or get it added to the applications menu either.

---

### Post by hyper_ch on 2008-02-01
Isn't Eclipse in the repositories?

If not, it depends how you install it. Mostly you'll get a .tar.gz file which contains all the source. You will have to compile that manually, normally done by this tria of commands

```

./configure
make
sudo make install

```
First however you need to get the compiler tools and required libraries installed.. otherwise it will fail

Sometimes you get premade binaries that you then need to run

```

./install.bin

```

or maybe

```

sh install

```

When you normally unpack those, there should be a text file containing instruction on how to "install"

---

### Post by gvartser on 2008-02-01
There is an easier way of installing then manually.

You have 2 options:

**Option 1: Simple:**
1) System -> Administration -> Synaptic Package Manager.

2) Click on search and enter:
   eclipse

3) Choose install.
[B]
Option 2: Also simple:[/B]
1) Open up a terminal window.

2) Execute the following syntax:
```
sudo apt-get install eclipse
```

/g

---

### Post by Telescope_Nerd on 2008-02-01
This is the link you need
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
it explains all about getting packages from the repositries or if they're not there, how to build from source, which is what you are trying to do.

---

### Post by philinux on 2008-02-01
The version in the repo is an earlier one. 

This link will help you in the future.

[http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

---

### Post by jan quark on 2008-02-01
everything correct

read this
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

it's a good compendium on how to install things in ubuntu

someone faster than me...impossible :)

---

### Post by Mosod on 2008-02-01
Much thanks for the help.  Particularly the monkeyblog.org link.  It looks like that does indeed have the info I'm looking for.  I do still have one question though.  Where should I put Eclipse?  I'm not terribly familiar with the Linux directory scheme.  Is /opt the right place if I want all users to have access to it?

---

