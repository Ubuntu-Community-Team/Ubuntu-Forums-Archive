---
title: "Recovering /bin/sh remotely"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ikebowen on 2008-01-09
So - for some silly reasoning that I'd be ashamed to admit to (beginner...), my /bin/sh is gone. Or, well, it exists, but is empty. The trick is that this is a headless box several hundred miles from here - any ideas on recovering the thing?

Any and all help would be appreciated. A lot. >.< Thanks...

---

### Post by geirha on 2008-01-09
By default /bin/sh is a symlink to /bin/dash, so it really depends on how you destroyed it. If you still have /bin/dash around and working, then you simply recreate the symlink: 

```

# Can't make the symlink if /bin/sh allready exist, so move it away somewhere
sudo mv /bin/sh ~/bin_sh_not_working
sudo ln -s dash /bin/sh
```

If dash also is gone, you can have it point to bash, which I assume you still have? same procedure as above, except replace dash with bash, and also, run ```
sudo aptitude reinstall dash
``` to reinstall dash

EDIT: For reference, here's /bin/*sh on my gutsy-box:
```
$ ls -l /bin/*sh
-rwxr-xr-x 1 root root 701680 2007-10-05 16:37 /bin/bash
-rwxr-xr-x 1 root root  80308 2007-09-29 14:47 /bin/dash
lrwxrwxrwx 1 root root      4 2007-10-26 00:13 /bin/rbash -> bash
lrwxrwxrwx 1 root root      4 2007-04-12 17:12 /bin/sh -> dash

```

---

### Post by ikebowen on 2008-01-09
Oi, that... ha. I was expecting /bin/sh to be something complicated and compiled and probably impossible to recover. Learned something new.

I recreated the symlink with sudo ln -s dash /bin/sh, and all's well. Thank you!

---

