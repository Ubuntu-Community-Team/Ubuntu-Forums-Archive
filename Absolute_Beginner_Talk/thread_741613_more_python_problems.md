---
title: "more python problems"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by vickenyon on 2008-03-31
hi all,
it seems i've come across a problem that i can't find a preexisting solution for on these here bbs. i have recently upgraded python to 2.5 and i can't seem to find a way to get 'ol cantankerous (my linux box) to recognize the path. python comes pre-installed in the /usr/bin directory, however, the new install places python in the /usr/local/bin directory. i would like to make python 2.5 the default but i am incapable and getting nowhere slowly. i've tried using a PATH in the .bashrc to point to the new version with no luck. thanks for any and all help in advance. victor.

---

### Post by jrib on 2008-04-01
What version of ubuntu are you using?  The latest stable release (Gutsy) has python2.5.

---

### Post by forrestcupp on 2008-04-01
Maybe instead of putting
```
#!/usr/bin/python
```
at the top of your code, you could just put
```
#!/usr/local/bin/python
```
there.  But that probably wouldn't make it easy to run on someone else's computer.

---

### Post by Cypher on 2008-04-01
Official Ubuntu packages won't install themselves into /usr/local/bin. That directory is usually left for users to install their own custom binaries. All official packages will go into /bin, /sbin, /usr/bin and /usr/sbin..

---

### Post by vickenyon on 2008-04-01
re: OS, i am running an older red hat that came with python 2.2

i would like to reiterate that i am trying to somehow reset the path for python so all other programs (excluding those i write) know where to find it. thanks again.

---

### Post by forrestcupp on 2008-04-01
You really should probably go to some Red Hat forum, then.  They set things up differently than Ubuntu does.

---

