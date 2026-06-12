---
title: "linking a directory to different partition?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by davidpbrown on 2007-08-26
I thought I'd keep windows programs (~/.wine/drive_c) on a separate partition save using up space on /home.

I expected that adding a pointer in /etc/fstab for the partition would then magically include those files in the directory structure but they weren't then visible in ~/.wine. This is how I imagined those pointers for other partitions like /usr and /usr/local worked.

Why didn't adding a pointer in /etc/fstab work? Do I need to create a ??symbolic link for the directory in the ~/wine pointing to the /media/windows-programs instead and if so how do I do that?

---

### Post by aidanr on 2007-08-26
[better way]("http://wiki.winehq.org/wineprefixcreate")

edit:// as far as i can tell it would work like this
```
mv ~/.wine /media/windows-programs/
wineprefixcreate --prefix /media/windows-programs/
```

---

### Post by davidpbrown on 2007-08-26
Thanks I'll try that for wine.. but more generally is it possible to assign any directory to a partition and how is that done, if it's not by adding the partition mount to the directory in fstab?

---

### Post by aidanr on 2007-08-26
yeah sure, but it's not working for you so you must have gone wrong somewhere, try mounting it manually first and once you get that working _then_ add it to fstab to have it done automatically on boot

---

