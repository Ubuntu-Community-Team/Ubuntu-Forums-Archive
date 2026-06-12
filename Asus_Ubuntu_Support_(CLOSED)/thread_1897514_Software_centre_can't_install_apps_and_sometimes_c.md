---
title: "Software centre can't install apps and sometimes crashes the whole computer."
date: 2011-12-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mapexmbirch on 2011-12-19
I have a problem with installing apps I get a unhandled error or something like that, here are the details.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the libiodbc2 package. This might mean you need to manually fix this package.

Problem with aptdaemon?

I think it started after the software centre crashed and loads of white text was scrolling down the screen on a black background. The software centre takes about a minute to open, Is this normal?

I have a netbook with 2GB of RAM, a 40GB SSD and 1.6GHz intel atom.

---

### Post by jerrrys on 2011-12-20
Open a terminal and enter (one at a time):

sudo dpkg --configure -a
sudo apt-get install -f

this will attempt to fix broken packages

---

