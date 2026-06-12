---
title: "Installing True Basic in Ubuntu"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by kenanton on 2007-10-20
I am trying to installing True Basic in Ubuntu Linux 7.10. I am using the Linux install files from the True Basic Annual 2002 disk.

When I run the tbinst program I get the following error message:

Installing True BASIC Language System in /usr/local/bin/ cp: cannot create regular file `/usr/local/bin/xtru': Permission denied

Is there any way around this problem? Is there any newer version of True Basic for Linux?

Thanks

---

### Post by kellemes on 2007-10-20
Don't know anything about true-basic..
The permission-issue is probably because you need to run the installer as root.
Try this: "sudo tbinst"

By the way.. have you looked at [Gambas]("http://gambas.sourceforge.net/")?

---

### Post by Frak on 2007-10-20
Try [Gambas]("apt:gambas") instead, it'll save you alot of trouble.

---

