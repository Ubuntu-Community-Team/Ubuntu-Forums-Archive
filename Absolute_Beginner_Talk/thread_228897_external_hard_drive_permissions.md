---
title: "external hard drive permissions"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by joethesmith on 2006-08-03
how to i set permissions so that i can write/delete on the 3 external hard drives that are on my desktop?

thanks
Joe

(its only my 3rd day of using ubuntu or any kind of linux :mrgreen: )

---

### Post by gilgongo on 2006-08-03
Are any of them NTFS formatted drives? If so, you really souldn't be writing to them as it'll cause large problems.

If they are EXT3 (ie Linux) formatted drives, then there's various way of doing this, but I don't know what the "correct" way is.

Perhaps somebody out there knows?

---

### Post by christhemonkey on 2006-08-03
You can fairly reliably write to NTFS now.
Using the ntfs-3g driver;
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

If they are in another format, then they should be easier to access.
(unless they are in some really obscure format.... but thats unlikely)

---

### Post by joethesmith on 2006-08-03
they are both NTFS drives, I will give ntfs-3g a shot, 

thanks
Joe

---

