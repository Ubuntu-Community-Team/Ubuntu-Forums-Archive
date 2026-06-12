---
title: "LIBX files"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by traveler-1 on 2007-07-03
How do I resolve the following.

libXaw.so.7 is needed by ICAClient-10.6-1.i386
        libXm.so.3 is needed by ICAClient-10.6-1.i386
        libXt.so.6 is needed by ICAClient-10.6-1.i386
        libXmu.so.6 is needed by ICAClient-10.6-1.i386
        libX11.so.6 is needed by ICAClient-10.6-1.i386
        libSM.so.6 is needed by ICAClient-10.6-1.i386
        libXpm.so.4 is needed by ICAClient-10.6-1.i386
        libXp.so.6 is needed by ICAClient-10.6-1.i386
        libXext.so.6 is needed by ICAClient-10.6-1.i386
        libICE.so.6 is needed by ICAClient-10.6-1.i386
        libdl.so.2 is needed by ICAClient-10.6-1.i386
        libc.so.6(GLIBC_2.3) is needed by ICAClient-10.6-1.i386
        libpthread.so.0 is needed by ICAClient-10.6-1.i386
        /bin/sh is needed by ICAClient-10.6-1.i386

Could not find them listed in synaptic and not sure at all about the last line.

Thanks in advance.:)

---

### Post by christhemonkey on 2007-07-03
For the last line, what is the output of this command:
```
ls -l /bin/sh 
```
Mine point to /bin/dash.

And for the other  things, working through 1 by 1:
libXaw.so.7 provided by libxaw7
libXm.so.3 - libmotif3
libXt.so.6 - libxt6
ibXmu.so.6 - libxmu6
libX11.so.6 - libx11-6
libSM.so.6 - libsm6
libXpm.so.4 - libxpm4
libXp.so.6 - libxp6
libXext.so.6 - libxext6
libICE.so.6 - libice6
libdl.so.2 - libc6
libc.so.6 - libc6
ibpthread.so.0 - libc6

In future check out packages.ubuntu.com the "Search the contents of packages" search.

---

### Post by traveler-1 on 2007-07-03
> **christhemonkey said:**
> For the last line, what is the output of this command:
```
ls -l /bin/sh 
```

Here it is
lrwxrwxrwx 1 root root 4 2007-07-01 09:58 /bin/sh -> dash

Thanks for the other tip.


Mine point to /bin/dash.

And for the other  things, working through 1 by 1:
libXaw.so.7 provided by libxaw7
libXm.so.3 - libmotif3
libXt.so.6 - libxt6
ibXmu.so.6 - libxmu6
libX11.so.6 - libx11-6
libSM.so.6 - libsm6
libXpm.so.4 - libxpm4
libXp.so.6 - libxp6
libXext.so.6 - libxext6
libICE.so.6 - libice6
libdl.so.2 - libc6
libc.so.6 - libc6
ibpthread.so.0 - libc6

In future check out packages.ubuntu.com the "Search the contents of packages" search.

a

---

