---
title: "Using Ubuntu 11.04 to backup user data from MacOS hard drive"
date: 2011-06-28
forum: Any Other OS
---

### Post by diablo75 on 2011-06-28
A new client has given me a Macbook Pro laptop that has crashed due to some major update failing (user interupted it and now the system won't boot).  I've tried all the standard remedies such as using the Disk Utility to check for errors, verify the drive, verify permissions, repair permissions, but the system still just hangs at the startup screen with the Apple logo.

What I would like to do is backup all the users files from the hard drive and use their install discs to format the drive and install from scratch.

I was able to boot Ubuntu 11.04 on this Macbook last night with absolutely no problems and can navigate the drive fine, but I'm running into file permission issues and need someway to change ownership of the files or at least gain read-only access so I can copy their stuff to an external hard drive.

Any idea how to do this?

---

### Post by mips on 2011-06-28
A very quick google for 'Ubuntu Mac HFS permission problem' yields this,

[http://ubuntuforums.org/showthread.php?t=1031842](http://ubuntuforums.org/showthread.php?t=1031842)
[http://ubuntuforums.org/showthread.php?t=1748566](http://ubuntuforums.org/showthread.php?t=1748566)

If you want write access you will have to disable journalling on HFS.

---

### Post by diablo75 on 2011-06-28
gksu nautilus

I should have known.  #-o

Thanks a million!

---

