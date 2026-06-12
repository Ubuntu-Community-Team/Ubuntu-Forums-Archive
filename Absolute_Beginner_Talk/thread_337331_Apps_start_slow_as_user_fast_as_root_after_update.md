---
title: "Apps start slow as user fast as root after update"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-01-12
Hi,

On Xubuntu 6.10 (Edgy Eft).

I just ran Update Manager and downloaded a bunch of updates, and afterwards noticed that my applications open slowly.  When I run them as root though, they open quickly.  This also applies to small, command line apps like vim as well.  It takes about 9 second for vim to open and 12 for gvim (gtk wrapper for vim).  Firefox it takes about 17 seconds.  

Anybody have this as well?  How do we fix it?  

Thank you.

---

### Post by x1a4 on 2007-01-13
Nevermind, fixed it.

Looks like windows has its uses.  I booted to windows to kill some vampires for a while.  Blood-lust satisfied, I booted back to XUbuntu.  When I logged Xfce told me it may not work right because it can't resolve the IP address (or something to that effect), then recommended I add my computer to */etc/hosts*.  

As my */etc/hosts* file was incorrect, I imagine one of the updates (don't ask me which) caused the change.  

Once I corrected */etc/hosts* and restarted Xfce, things went back to normal.

---

