---
title: "Anyone want to be the guinea pig and help me mke a tutorial on how to compile Pidgin?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by kevdog on 2008-01-03
I know there exists a tutorial for Gutsy how to compile pidgin from source, however this will not always work for me and definitely not for previous versions (Feisty, Edgy, etc.).  

Personally Ive managed to download and compile Pidgin on 3 machines now, however struggled to get the correct dependencies.  I should have written down all the proper dependencies, however at the end of every process, I had gotten lazy and came up with an incomplete list. 

I was wondering if anyone would like to take this step and attempt to install pidgin from scratch.  I will definitely walk you through the process, in addition to helping you install additional plugins if necessary (purple plugin pack, encryption, etc).  I'm trying to compose a How-To for this process.  I could probably do this right now, however could not confirm if this How-To is accurate.

Anyone game?

---

### Post by RomeReactor on 2008-01-03
Hi. Just a thought, but why not do:
```
sudo apt-get build-dep gaim
```
on Feisty or previous systems to sort out the dependencies?

---

### Post by Lostincyberspace on 2008-01-03
I will do it just let me get my feisty virtual server set up. I should be fine in 30-40 minutes

---

### Post by kevdog on 2008-01-03
That will work for the basic setup, however will not install all of the extra packages needed if you want to add nm-support, cyrus, mono, tcl, tk, dbus, etc.  These options needed to be specified on the ./configure line.  I cant remember all the libraries needed to activate these options.  Im looking for an all inclusive tutorial beyond the basics

---

### Post by iansane on 2008-01-03
add/remove> pidgin

applychanges

lol

---

### Post by kevdog on 2008-01-04
If anyone is interested please send me a private message.  Im going to bed but will be ready for this tomorrow.  If you know the basics about compiling programs, it shouldnt take too long (and you will get credit in the HOW-TO).

---

### Post by kevdog on 2008-01-04
I guess I got no takers in the Beginners Forum, possibly I should try elsewhere.

---

