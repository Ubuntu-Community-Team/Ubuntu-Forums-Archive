---
title: "&quot;Reboot Workaround?&quot; OR &quot;I'm a Dope, Can You Help?&quot;"
date: 2009-10-21
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2009-10-21
I have a new-ish MBP, and as many have encountered, Jaunty doesn't reboot the newer MBPs.

[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Reboot](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#Reboot)

It's been this way since I first downloaded in April, and I'm kind of surprised it hasn't been fixed in an update yet.

Regardless, I'm dumb. I regularly hit "Restart" then think "Duh, I shouldn't have done that." Is there some way to replace or modify the Restart command to a Shut Down command?

Additionally, I noticed when fsck self-executed this morning that it automatically restarts (which also doesn't work). If there were a temporary patch to redirect the Restart call to a Shut Down call (as in a global sense, not just from the desktop) that could be beneficial. Any thoughts?

---

### Post by Bachstelze on 2009-10-21
> **teamjh14 said:**
> Any thoughts?

Upgrade to Karmic. :)

---

### Post by crocowhile on 2009-10-21
It's the kernel. 2.6.31 restarts without problems.
If you don't want to upgrade kernel, install kexec-tools for a partial workaround.

---

### Post by Tu1J4kXk8NUhMz on 2009-10-21
Heh. I didn't even bother to look and see when Karmic came out. Why bother?

Thanks y'all!

---

