---
title: "unusual error message"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by friedokra on 2006-08-07
Everytime I install a new program, I get this type of error message: 

"E: python2.3-4suite: subprocess post-installation script returned error exit status 2"

and in the terminal I get something similar. Programs seem to work fine after they are installed, but I get this error message every install. Any ideas what this could be?

---

### Post by friedokra on 2006-08-07
I'll post more about this later. I want to post what is going on in terminal when this happens.

---

### Post by friedokra on 2006-08-08
bump

---

### Post by friedokra on 2006-08-08
Here's another example after trying to install beagle!

-------------------------------------------------------------------------__
Errors were encountered while processing:
 python2.3-4suite
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python2.3-4suite (0.99cvs20050418-2ubuntu1) ...
Can't list /usr/lib/python2.3/site-packages/Ft
Can't list /usr/lib/python2.3/site-packages/Ft
update-alternatives: unable to make /usr/share/4Suite/4ssd.dpkg-tmp a symlink to /etc/alternatives/4ssd: No such file or directory
dpkg: error processing python2.3-4suite (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.3-4suite
clay@clay-laptop:~$

---

### Post by tony_tj3 on 2006-08-08
you could try to go into synaptic, and check the broken filter (bottom left corner click custom>>broken), see if python2.3-4suite is there, if it is, mark it for complete removal and apply. If it's not there, try the marked changes filter. I had the same problem a while ago with a different package, i beleive that is what i did to fix it...

---

