---
title: "transcode installation problem"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by maneesh on 2006-12-18
Hi, I am trying to install transcode in my edgy installation. Facing following problem, any idea ??


~# apt-get install transcode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  transcode: Depends: libavcodec51d (>= 0.svn20060811) but it is not going to be installed
             Depends: libmp3lame0 but it is not going to be installed
             Depends: libpostproc51d (>= 0.svn20060811) but it is not going to be installed

---

### Post by dbbolton on 2006-12-18
what happens if you try it as root ?

---

### Post by maneesh on 2006-12-23
I tried this with root only.

---

