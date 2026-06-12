---
title: "Installation help"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by rugbydazzla4 on 2007-05-11
I recently tried, installing limewire and it hung half way through and i couldnt get it to quit so just shut down my laptop...now whenever i try and install/remove anything through add/remove or synaptic manager i get this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i have no idea how to solve this (or what it even means :S)


any help please?

---

### Post by pizzutz on 2007-05-11
Your limewire install failed before it was properly configured.  apt-get will be frozen till it is finished.  Just do what it says "sudo dpkg --configure -a" (basically means manually configure all packages that aren't configured)  If it doesn't solve the problem, give us any error messages, and we will help you.

---

### Post by rugbydazzla4 on 2007-05-11
okay, ran that command in terminal and got this message

dpkg: requested operation requires superuser privilege

---

### Post by pizzutz on 2007-05-11
```
sudo dpkg --configure -a
```make sure you prefix it with "sudo" and type in your password.

---

### Post by rugbydazzla4 on 2007-05-11
thanks for ur help! that sorted it all out.

but now when i load up limewire, the loading screen comes up and just says "loading html engine" and has been doing so for abotu 5 minutes and i cant minimise it/close it or anything it. :S

---

### Post by rugbydazzla4 on 2007-05-11
ignore that, got it sorted
thanks for your help!

---

