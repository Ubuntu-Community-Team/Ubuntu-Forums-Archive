---
title: "problem while trying to update gutsy (7.10)"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by corn89 on 2007-11-03
When i installed, i connected to the internet to get the latest updates.
When i started the update manager, it said it had 92 updates, and it stated downloading them untill it got to the 82nd update, then it gave me this error message:
"E: tzdata: subprocess post-installation script returned error exit status 10"
In the details below the update progress it says this:

extracting templates from packages: 100%
preconfiguring packages . . .
setting up tzdata (2007h-Qubuntu0.7.10)
dpkg: error Processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. trying to recover:
setting up tzdata (--configure):
subprocess post-installation script returned error exit status 10

anybody know how to fix this?

---

### Post by tchoklat on 2007-11-03
It sounds like it cannot install a package called tzdata. [SIZE=2]**TZDATA** reads a time zone definition file given in either text format or processed (binary) format. Try to do a apt-get remove tzdata then update manager again. You never know![/SIZE]

---

