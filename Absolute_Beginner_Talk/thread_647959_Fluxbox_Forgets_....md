---
title: "Fluxbox Forgets ..."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by buzzbo on 2007-12-22
I have followed most of [COLOR=Red][RedSquirrel's HOWTO on getting fluxbox menus]("http://ubuntuforums.org/showthread.php?t=371144")[/COLOR], and have a pretty good setup.  I am happy with my menus, and am able to change styles.  However, if I try to rename my Workspaces, or add workspaces, these disappear when I restart fluxbox.  Any idea what's going wrong here?

Thanks,
Buzz

---

### Post by buzzbo on 2007-12-23
OK I frequented the #fluxbox IRC channel, and discovered that my ~/.fluxbox/init file was read-only.

The bottom line is:
~/.fluxbox should be at least **read/write/exec** by the user
~/.fluxbox/[files] should be at least **read/write** by the user 

- Buzz

---

