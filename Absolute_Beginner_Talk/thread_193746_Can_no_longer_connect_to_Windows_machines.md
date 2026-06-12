---
title: "Can no longer connect to Windows machines"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by gratefulfrog on 2006-06-10
Hi!

Since upgrading to Dapper on (AMD64), I can no longer see the Windows machines on "Wiondows Network" in the Gnome file browser.  I get this error message: "smb:///" is not a valid location.

This used to work fine on Breezy (AMD64).

I can however mount the windows shares, though using:
$ sudo smbmount //PC-machine/share ./mnt

Any ideas?

---

### Post by tronica on 2006-06-10
i had something simalar:

[http://ubuntuforums.org/showthread.php?t=140125](http://ubuntuforums.org/showthread.php?t=140125)

hopefully that will do the trick.

---

### Post by gratefulfrog on 2006-06-11
[QUOTE=tronica]i had something simalar:

[http://ubuntuforums.org/showthread.php?t=140125](http://ubuntuforums.org/showthread.php?t=140125)

hopefully that will do the trick.[/QUOTE]

Thanks!  That did it! 

The Ubuntu community is a breath of fresh air for humanity!
Cheers,
FG

---

