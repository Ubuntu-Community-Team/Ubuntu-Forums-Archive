---
title: "Help!!! I Need To Compile!!!"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by kevin11951 on 2007-07-11
i am beginner to the world of linux, and would like to compile "pidgin" from source as a test... but when ever i try to compile anything it spits it back up missing glib, and so i found the -dev in the repos. now when i run ./configure it wants gtk, which i cant find. it also wants: No package 'atk' found
No package 'pango' found
No package 'cairo' found... HELP!!! is there something i can install with everything i need. help!

---

### Post by KIAaze on 2007-07-11
You'll probably need those packages:

libcairo2
libcairo2-dev

libpango1.0-dev
libpango1.0-common
libpango1.0-0

libatk1.0-0
libatk1.0-dev

libgtk2.0-0
libgtk2.0-common
libgtk2.0-dev

libglib2.0-0
libglib2.0-dev

Maybe not all are necessary, but you'll need at least one of each I think, especially the -dev files (as far as I know, they contain the headers necessary for compiling).

---

### Post by KIAaze on 2007-07-11
posting error

---

### Post by pyros on 2007-07-11
> **kevin11951 said:**
> i am beginner to the world of linux, and would like to compile "pidgin" from source as a test... but when ever i try to compile anything it spits it back up missing glib, and so i found the -dev in the repos. now when i run ./configure it wants gtk, which i cant find. it also wants: No package 'atk' found
No package 'pango' found
No package 'cairo' found... HELP!!! is there something i can install with everything i need. help!

try opening a terminal and typing
```

sudo apt-get build-dep pidgin

```
that should install all of the build (compile) dependencies of pidgin.

---

### Post by KIAaze on 2007-07-12
Nice. :)
I didn't know that.

---

### Post by pyros on 2007-07-12
> **KIAaze said:**
> Nice. :)
I didn't know that.

yeah, it's super handy.

---

### Post by Ek0nomik on 2007-07-12
> **pyros said:**
> try opening a terminal and typing
```

sudo apt-get build-dep pidgin

```
that should install all of the build (compile) dependencies of pidgin.

The only reason that works is because the dependencies are known from the repository, correct?

If I had software that wasn't in the repository, that command wouldn't spit out the needed dependencies I take it?

Is there any sort of tool that shows you all the dependencies needed from the software before you compile it?  Or is that strictly reliant on being given to you in the README information?

---

### Post by pyros on 2007-07-12
pretty much, it is dependent upon the developer or packager.

---

### Post by Ek0nomik on 2007-07-12
> **pyros said:**
> pretty much, it is dependent upon the developer or packager.

That's what I figured.

I have found some software to be a real pain to compile because the dependencies aren't clearly laid out.

Verlihub is the example that comes off the top of my head.  That was such a pain to install because I had no idea what I needed to compile the thing.

Anyways, thanks.  :)

---

