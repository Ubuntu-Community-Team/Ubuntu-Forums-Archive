---
title: "cifs-utils missing"
date: 2020-12-02
forum: Apple Hardware Users
---

### Post by leeep on 2020-12-02
Hi.  I'm brand new to Ubuntu.  Just installed it on a Mac.  I want to access data stored on a Mac airport - not the time machine data, but data stored in a directory on the airport.  I got as far as needing to mount it, but my install (20.04.1 LTS) doesn't seem to have the utils.  I tried to install cifs-utils but I got this:


sudo apt-get install cifs-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cifs-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'cifs-utils' has no installation candidate


I've been on Google for an hour or so, but can't fix it.  I tried apt-key update but got a message that this command can only be used by root.  

Any idea how I can get cifs-utils?  If there's an easier way to get at the files on my Mac Airport then that would also be useful.

Thanks, 

Lee

---

### Post by ActionParsnip on 2020-12-02
[https://packages.ubuntu.com/focal/cifs-utils](https://packages.ubuntu.com/focal/cifs-utils)

It is present. Check your sources

---

### Post by wildmanne39 on 2020-12-02
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by leeep on 2020-12-02
Thanks, ActionParsnip.  I think I've got it loaded now. I suspect I'll  be back soon after Apple's airport disc has browbeaten me into submission.

---

