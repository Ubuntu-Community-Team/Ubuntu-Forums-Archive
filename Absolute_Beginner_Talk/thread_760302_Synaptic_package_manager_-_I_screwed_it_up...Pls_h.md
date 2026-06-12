---
title: "Synaptic package manager - I screwed it up...Pls help"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by imari2542 on 2008-04-20
I was trying to get wicd and when I typed in the command as I thought was correct I screwed up the snyaptic package manager.

When I try to open it, I get the following error message:

E: Malformed line 79 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

How can I fix this please???

---

### Post by jimbren on 2008-04-20
can you post the contents of your sources.list file?

```
gedit /etc/apt/sources.list
```

---

### Post by imari2542 on 2008-04-20
I figured out I needed to remove line 79 which I did, now I get this error:

W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071016)_dists_gutsy_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071016)_dists_gutsy_restricted_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071016)_dists_gutsy_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071016)_dists_gutsy_restricted_binary-i386_Packages)

Any ideas???

---

### Post by imari2542 on 2008-04-20
I clicked ok after the error message...reloaded and closed and restarted synpatic and all was OK....Thanks anyway

Now if I could just get the wireless to work....
[http://ubuntuforums.org/showthread.php?p=4750669#post4750669](http://ubuntuforums.org/showthread.php?p=4750669#post4750669)

---

