---
title: "[SOLVED] linux-image-2.6...needs to be reinstalled but can't"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by xIke on 2007-11-03
Whenever I run apt-get upgrade, I get this error:

```
E: The package linux-image-2.6.23.1 needs to be reinstalled, but I can't find an archive for it.
```

I've been trying to compile a new linux kernel to fix my suspend issues, and have had no luck due to fglrx.  I assume that this has something to do with kernelcheck.  Does anyone know how I can fix this?

Thanks!

---

### Post by haldean on 2007-11-03
Uninstall the linux-image-2.6.23.1 package and install the latest kernel in the repositories, which is 2.6.22-14 - that should get rid of the error.

---

### Post by xIke on 2007-11-03
> **haldean said:**
> Uninstall the linux-image-2.6.23.1 package and install the latest kernel in the repositories, which is 2.6.22-14 - that should get rid of the error.

It gives me the same error if I try "sudo apt-get remove linux-image-2.6.23.1".  How can I get around this?

---

### Post by haldean on 2007-11-03
Well I would say try using dpkg --remove linux-image-2.6.23.1 but that could be a little dangerous. I'm pretty sure it would work, but I dunno - I wouldn't do it unless I had more than one kernel installed.

---

### Post by xIke on 2007-11-03
That complains about the package being in an "inconsistent state" and says that I should reinstall it first.

---

### Post by xIke on 2007-11-04
I ended up cleaning it up by force removing it.  This isn't normally advisable, but I knew what it had done and reversed that myself.

Cheers.

---

### Post by haldean on 2007-11-04
Great! Could you please mark the thread as solved, so people know that you've fixed the problem? (Thread Tools->Mark Thread as Solved) 
Thank you!

---

### Post by xIke on 2007-11-04
> **haldean said:**
> Great! Could you please mark the thread as solved, so people know that you've fixed the problem? (Thread Tools->Mark Thread as Solved) 
Thank you!

Done.  I never saw that before...I need to go back and fix quite a few threads now.  Thanks!

---

### Post by elec999 on 2007-11-19
I am getting this very error
I tried
dpkg: error processing linux-image-2.6.23.1 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 linux-image-2.6.23.1
how can i force remove it.
Thanks

---

### Post by xIke on 2007-11-19
I don't remember the exact syntax (not in Ubuntu right now.)  It's something like:

```
sudo dpkg --remove --force-remove-<packagename>
```

---

