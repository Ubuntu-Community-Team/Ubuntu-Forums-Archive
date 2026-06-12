---
title: "VMWARE was working, now won't start up ..."
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2008-01-15
When I try to start vmware, I get the following:

$ vmware

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)



How do I fix this?

Thanks

Carl

---

### Post by alexdbkim on 2008-01-16
Try to install libcairo first since the error message shows that vmware requires the library.

> sudo apt-get install libcairo2

Cheers,

---

