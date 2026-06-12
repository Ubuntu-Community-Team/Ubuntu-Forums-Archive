---
title: "Forcing FSCK disk-check on next reboot"
date: 2008-02-26
forum: Apple PPC Users
---

### Post by stream303 on 2008-02-26
Found an easy way to force a disk-check on the next reboot:

```
sudo touch /forcefsck
```

Now reboot the system.

When it comes back up, the forcefsck file is gone.

I tried the old *shutdown -F -r now* but it didn't work, and the -F option isn't listed in my shutdown man page.

I also changed a line in /etc/default/rcS to read:

FSCKFIX=yes

so that I wouldn't have to sit there and enter "y" every time it found an error to fix.  In my case, I didn't have any errors to fix, so I'm not sure this is needed, or if there could be a "fix all" option when fsck starts up.  But so far, so good!

---

