---
title: "what version of ndiswrapper am i running?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by insub2 on 2007-01-04
hello all,
awhile ago i put edgy on my laptop and had a bitch of a time getting wireless working.  I finally got my BCM4306 card working using ndiswrapper.  I used several different howto's and am not actually sure how i ended up getting it working.

...I want to try out Linux Mint.

i plan to back up my / partition and reconstitute it if anything goes wrong.  but i would like to figure out how i got wireless working to make it easier on myself when i install Linux Mint.


The short of it:
how do i find out which ndiswrapper version i am running?

---

### Post by bluefrog on 2007-01-04
open synaptic and look for ndiswrapper-utils in the right window, you will see the version number in the properties

James

---

### Post by insub2 on 2007-01-04
big negative partner.  I didn't use synaptic to install it... or so it would appear.  none of the ones shown are marked.

i scrolled up my commands in the terminal and found that i *wgot* [http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz](http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.28.tar.gz)


is there a way to double check that?

---

### Post by jpeddicord on 2007-01-04
This should do it (terminal):
```
modinfo ndiswrapper
```

---

### Post by insub2 on 2007-01-04
> **jacobmp92 said:**
> This should do it (terminal):
```
modinfo ndiswrapper
```

SWEET!!!
thank you mister.

---

