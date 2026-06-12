---
title: "I thought I *Was* the Root..."
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by MarkTBSc on 2006-03-29
Ok... This is on the same sort of thing as my earlier post but it's another facet. I've found out what to add to my xorg.conf file to make my screen work...

But now, whenever I try to edit the file, it won't let me. I can't access it in the console/terminal, I can't modify it in Gedit (it says it's read only and I'm not the owner) and I can't log in as the root because it won't let me log in on the intro screen. It says I'm not allowed.

If I go in on the troubleshooting command line then I can't access xorg.conf!!!

Help? Please?

---

### Post by earobinson on 2006-03-29
sudo gedit xorg.conf will work!

use sudo whenever you try to do a root command

---

### Post by aysiu on 2006-03-29
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by MarkTBSc on 2006-03-29
Ohhhh!!! So THAT'S what sudo means!!

I was wondering, seeing it everywhere.

Thanks!

---

### Post by MarkTBSc on 2006-03-29
Both very interesting and informative sites! Thank you.

---

### Post by aysiu on 2006-03-29
[QUOTE=MarkTBSc]Both very interesting and informative sites! Thank you.[/QUOTE] Glad it all worked out for you.

---

