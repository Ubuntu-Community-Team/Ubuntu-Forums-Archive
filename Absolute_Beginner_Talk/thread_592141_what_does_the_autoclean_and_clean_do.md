---
title: "what does the autoclean and clean do?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by maduranga on 2007-10-26
can someone tell me what does the following three commands do?

 sudo apt-get autoclean
 sudo apt-get clean

 sudo apt-get autoremove 


 thanks for advice,

---

### Post by forestpixie on 2007-10-26
autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

       clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect (8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

it's all in the manual :)

---

### Post by Maestro23 on 2007-10-26
> **maduranga said:**
> can someone tell me what does the following three commands do?

 sudo apt-get autoclean
 sudo apt-get clean

 sudo apt-get autoremove 


 thanks for advice,

[http://ubuntuforums.org/showthread.php?t=591467&highlight=apt-get+autoclean](http://ubuntuforums.org/showthread.php?t=591467&highlight=apt-get+autoclean)

> man apt-get

Tells you all about it.

---

### Post by maduranga on 2007-10-26
thanks :) didn't knew them.

---

