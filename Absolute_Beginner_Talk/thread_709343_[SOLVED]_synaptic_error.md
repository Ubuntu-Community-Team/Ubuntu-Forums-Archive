---
title: "[SOLVED] synaptic error"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-02-27
I was installing the newest version of Alexandria and my computer froze (it does that too often). I had to hit Alt+PrintScreen+B and reboot (I tried something else first - something I learned recently - Alt+PrintScreen+S). When I started Synaptic I got the "run dpkg --configure -a manually" error, so I ran it.
It told me something was wrong with the package Alexandria and it needed to be reinstalled, but the archives couldn't be found.
I tried installing it again (by downloading the .deb package) but got this error: > Could not open 'alexandria_0.6.3_all-2.deb'
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
I get an update notification, but when I click on it, I get this error message: > Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package alexandria needs to be reinstalled, but I can't find an archive for it.'
The only option I have is to hit the close button which, well, closes it.
I get this error message when I open Synaptic:
> E: The package alexandria needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
Again, all I can do is close.

So I get that I need to reinstall Alexandria, but how do I do that if nothing that installs packages will run??

And oh yeah, I tried ```
sudo apt-get install alexandria
```
Same error message: > E: The package alexandria needs to be reinstalled, but I can't find an archive for it.

How do I fix it?
Thanks.

---

### Post by forestpixie on 2008-02-27
try this

```
sudo dpkg --remove --force-remove-reinstreq alexandria
```

---

