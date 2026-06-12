---
title: "error pmk?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-10-11
why do I always get the error message when I install "pmk"

---

### Post by PriceChild on 2006-10-11
Could you paste the error message?

---

### Post by Frak on 2006-10-11
Setting up pmk (0.9.3s2-2) ...
dpkg: error processing pmk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pmk
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Frak on 2006-10-11
Setting up pmk (0.9.3s2-2) ...
dpkg: error processing pmk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pmk
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up pmk (0.9.3s2-2) ...
dpkg: error processing pmk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 pmk

---

### Post by .t. on 2006-10-11
It sounds like a bug in the deb's install scripts. File a bug against it here:
[http://bugs.ubuntu.com](http://bugs.ubuntu.com)

---

### Post by Frak on 2006-10-11
I have filed a bug, but still does anybody know how to fix it.

---

### Post by .t. on 2006-10-12
Could you post the number. If you are desperate, run "sudo aptitude build-dep pmk && sudo apt-get -b source pmk". The first installs any packages required for pmk to build properly (build dependencies), and the second downloads and builds the sources.

---

### Post by Frak on 2006-10-12
Bug #65567

---

### Post by Frak on 2006-10-12
Oh... I fixed the problem....
Reinstalled Ubuntu.
Works great now!

---

