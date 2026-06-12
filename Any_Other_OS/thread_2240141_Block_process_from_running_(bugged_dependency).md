---
title: "Block process from running (bugged dependency)"
date: 2014-08-18
forum: Any Other OS
---

### Post by 7dda243d on 2014-08-18
Hi, 
I have a problem where a file explorer calls on another package to generate thumbnails, and i have a directory full of huge video files, so tumblerd tries to make thumbnails and completely freezes the computer while it tries to.

How can i block 'tumblerd' from ever running, so if it get's called on from another program it's instantly killed?

(Please note i can not uninstall (?) tumblerd because it's a dependency of the file explorer, trying to uninstall, also uninstall's the file explorer)

Thank you

---

### Post by sotiris2 on 2014-08-18
You can disable thumbnails on thunar (this is the file manager.) Or according to [this (second from last post)](http://askubuntu.com/questions/89826/what-is-tumblerd) you can edit a configuration file to make it not generate thumbnails for video files only (and keep for images which should be less demanding). To do so you would do ```
sudo leafpad  [COLOR=#333333][FONT=UbuntuRegular]/etc/xdg/tumbler/tumbler.rc
``` and you ll probably find some entry for videos that you can switch from true to false (or from 1 to 0). Unfortunately I don't use xfce so I don't now exactly what will be inside. If unsure of what to do post the contents here.[/FONT][/COLOR]

---

### Post by 7dda243d on 2014-08-18
I'm actually using elementary OS, which uses 'pantheon files'. I've been looking for a way to disable thumbnails in it, but i won't let you. (Did not find the file specified using 'cd /' 'sudo find -name tumbler.rc')

Is it possible to constantly run a script loop that looks for tumblerd, and will a loop use allot of resources?

---

### Post by slickymaster on 2014-08-18
@7dda243d:
Since you say you're using elementary OS, I'm moving your thread to the **Other Operating Systems and Projects** sub-forum.

---

### Post by 7dda243d on 2014-08-18
Fair enough, but the distro was kind of off topic, i was hoping for something that could be applied to any linux for blocking processes from running,

is a shell script loop an optimal good solution?

---

