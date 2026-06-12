---
title: "VMWare broken..."
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-02-16
I recently did a dist-upgrade to update my PC
Now my vmware is not working
I know that I upgraded the linux-686/386-image
Do I have to do a ./configure for my vmware or something?

When I try to launch it nothing happens...

Any ideas?

---

### Post by jonathan.lees on 2007-02-16
try

```

sudo /usr/bin/vmware-config.pl

```

---

### Post by charles.g.moore on 2007-02-19
Thanks, I looked around and found that once I update the headers VMWare requires a re-configuration.

---

