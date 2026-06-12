---
title: "Help needed installing Hamachi"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Terry@nz on 2008-02-29
Linux 7.10
I'm new to Linux, though not to computers.

Installing Hamachi I followed the instructions at [http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)
All went well until: hamachi-init.
I got the response: -

hamachi-init: error while loading shared libraries: libcrypto.so.0.9.7: cannot open shared object file: No such file or directory.

Actually there is such a file - it's in one of the VMware folders. Would this be what hamachi is looking for? and how do I go about telling hamachi where it is? I tried copying it to the hamachi folder, but that didn't help.

BTW I'm not sure if I am using the right version of hamachi: - my processor is an AMD Duron, not a Pentium. Anyone know if the Pentium version is correct?

Terry@nz

---

### Post by SOULRiDER on 2008-02-29
Try with this
```
sudo aptitude install libcrypto0.9.8-udeb
```

---

