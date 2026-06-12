---
title: "Dual boot Retina Mid-2015 15 Hangs on shutdown"
date: 2016-02-20
forum: Apple Hardware Users
---

### Post by zudduz on 2016-02-20
I was issued a Retina Mid-2015 15.  I set  it up to dual boot and now Ubuntu 15.10 Hangs on shutdown.
I removed quiet splash and It printed:
```
[ OK ] Stopped Create Volatile Files and Directories
[ OK ] Stopped target  Local File Systems.
      Unmounting /boot/efi...
      Unmounting /run/user/119...
      Unmounting /run/cgmanager/fs...
      Unmounting /run/user/1000/gvfs...
[ OK ] Unmounted /run/user/119.
[ OK ] Unmounted /run/cgmanager/fs.
[ OK ] Unmounted /boot/efi.
[ OK ] Unmounted /run/user/1000/gvfs.
      Unmounting /run/user/1000...
[ OK ] Unmounted /run/user/1000.
[ OK ] Reached target Unmount All Filesystems.
[ OK ] Stopped target Local File Systems (Pre).
[ OK ] Stopped Create Static Device Modes in /dev.
[ OK ] Stooped Remount Root and Kernel File Systems.
[ OK ] Reached target Shutdown.
[   48.537649] reboot: Power down 
```

Once that's printed nothing else happens other than the computer getting pretty warm and the fan turning on.

---

### Post by gtoosla on 2016-08-14
Same here

---

### Post by lstewart4 on 2016-08-20
Same. Did either of you find a solution to having blank screen after waking from suspend (or experience this problem?)

---

