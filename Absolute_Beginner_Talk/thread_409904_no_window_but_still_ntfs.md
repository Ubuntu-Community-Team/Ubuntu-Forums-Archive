---
title: "no window but still ntfs"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-04-15
Hi all,

I have a ntfs partition but no window. and the last time i used windows i didnt shut it down properly. so now my partition wont mount. i tried to run ntfs fix but i get:
```

~$ ntfs-3g /dev/hdc1 /media/media -o force
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdc1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
   the 'force' option read-write, or with the 'ro' option read-only.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

```

what can i do?:confused: 
i cant see a solution without windows.

ta,
nolander.

---

### Post by jvc26 on 2007-04-15
> 
   Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
   the 'force' option read-write, or with the 'ro' option read-only.

Isn't that the linux solution?

ntfsfix is one word, and at a guess:
```

man ntfsfix

```
Will tell you the proper usage for ntfsfix
Il

---

