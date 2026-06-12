---
title: "[SOLVED] Update manager error"
date: 2007-09-24
forum: Apple Intel Users
---

### Post by themacmonk on 2007-09-24
I seem to be getting this error message.

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing xfce4-xfapplet-plugin (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened."

I've tried the solutions from similar threads but with no results.  I haven't installed anything new so I'm not sure what the problem is.

I'm using a 2.0 gHz MacBook (not the pro).

Thanks!

---

### Post by cyberdork33 on 2007-09-24
> **themacmonk said:**
> I seem to be getting this error message.

"A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing xfce4-xfapplet-plugin (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened."

I've tried the solutions from similar threads but with no results.  I haven't installed anything new so I'm not sure what the problem is.

I'm using a 2.0 gHz MacBook (not the pro).

Thanks!
Sounds like a software issue. Did you post your error to the bug?

Your package list file may be corrupted or something. Have you tried running update commands manually?

Try:
```
sudo apt-get update
``` and note any error messages.

---

### Post by themacmonk on 2007-09-25
Thanks for the reply.

Yes I did try to do it manually and get the same thing:

E: Dynamic MMap ran out of room
E: Error occurred while processing xfce4-wavelan-plugin (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Strange thing is, I haven't installed anything new.  The error just appeared recently.

---

### Post by cyberdork33 on 2007-09-25
> **themacmonk said:**
> Thanks for the reply.

Yes I did try to do it manually and get the same thing:

E: Dynamic MMap ran out of room
E: Error occurred while processing xfce4-wavelan-plugin (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Strange thing is, I haven't installed anything new.  The error just appeared recently.
You don't have to actually install anything. The system gets a new package list from the server, then checks the package list for newer packages than what you have installed in order to let you know that there are updates available. I am thinking this package list file has become corrupted, and thus the package managers cannot read it anymore.

I would delete the /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages file (probably need sudo to do that) and then try the update command again. That will attempt to download a fresh file again.

---

### Post by themacmonk on 2007-09-25
Yes!  That worked!

Great support from this forum as always.

---

### Post by cyberdork33 on 2007-09-25
please mark as solved

---

