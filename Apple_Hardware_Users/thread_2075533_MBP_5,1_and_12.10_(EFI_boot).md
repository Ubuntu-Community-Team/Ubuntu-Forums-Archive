---
title: "MBP 5,1 and 12.10 (EFI boot)"
date: 2012-10-24
forum: Apple Hardware Users
---

### Post by SwedishWings on 2012-10-24
I can't figure out how to make the NVidia drivers work on 12.10. Anyone succeeded yet?

It seem like the the Xorg can't find the DMKS stuff in kernel after install:

```
[  1349.956] (EE) Failed to load module "nvidia" (module does not exist, 0)
```

I've tried nvidia-current, nvidia-current-updates and nvidia-experimental-304 but all with the same problem.



Btw, bcmwl-kernel-source do not work either, however, the default drivers do work as far as I can tell.

Regards,
Mike

---

### Post by SwedishWings on 2012-10-24
I found a solution:

[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/)

---

