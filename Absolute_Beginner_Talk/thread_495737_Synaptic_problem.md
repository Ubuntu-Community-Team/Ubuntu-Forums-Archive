---
title: "Synaptic problem"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-07-08
I was trying to install Frostwire .deb file last night and it wasn't working, now, when I go into synaptic it says 
```
E: The package frostwire needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```
I tried redownloading the same deb file from the website again and when i try installing it, it says:
```
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
```

Any help would be wonderful!

---

### Post by forestpixie on 2007-07-08
you might need to try to remove the package and then reinstalling, I think this is right

sudo dpkg --remove <package name>

I had to force the issue once with 

sudo dpkg --remove --force-remove-reinstreq <package name>

---

### Post by Bofur on 2007-07-08
That did it, thanks :guitar:

---

### Post by forestpixie on 2007-07-08
great I've used it a few times now!!!!! got me out of some holes

have alook at the manual for dpkg and apt-get I'm glad I did

man dpkg etc. etc. in terminal

:D

---

