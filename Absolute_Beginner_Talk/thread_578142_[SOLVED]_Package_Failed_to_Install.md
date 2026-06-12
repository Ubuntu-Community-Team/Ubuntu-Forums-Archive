---
title: "[SOLVED] Package Failed to Install"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-10-16
Aptitude shows 98 packages to be updated, but when I tell it to update it fails with the following errors
```

Preparing to replace audacious-plugins 1.3.5-3ubuntu2 (using .../audacious-plugins_1.3.5-3ubuntu4_i386.deb) ...
Unpacking replacement audacious-plugins ...
dpkg: error processing /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/audacious/General/libcurl.so', which is also in package audacious-plugins-extra
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/audacious-plugins_1.3.5-3ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

Is there a way to fix this one package so I can get the rest of the updates?

---

### Post by DSn0wMan on 2007-10-16
I just cleaned out the cache

apt-get clean

This got rid of the offending package, but it was just as broken on the second download.

audacious-plugins_1.3.5-3ubuntu4_i386.deb

---

### Post by DSn0wMan on 2007-10-16
solved [http://ubuntuforums.org/showthread.php?t=577878&highlight=audacious-plugins](http://ubuntuforums.org/showthread.php?t=577878&highlight=audacious-plugins)

---

