---
title: "find command without output of permission denided"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-10-31
Hi,
using Gutsy. I stared Terminal window and I would like to find a file in my disk. So executing command:
```
find / -name myfile
```
The output is fine, but I dislike to get 100 rows or more of 'Permission denied' files like:
find: /proc/6128/fdinfo: Permission denied

I also found out  ```
find / -name myfile | grep -v " Permission denied"
``` command displays permission denied lines. So doesn't work as I would like.

Any idea how to get output of find command without "Permission denied" lines??

Thanks,
Abcuser

---

### Post by macogw on 2007-10-31
use -vi with grep instead of just -v so it'll ignore case and catch both "Permission denied" and "permission denied"

---

### Post by spec-chum on 2007-10-31
To avoid seeing these you could redirect standard error to the null device.  This should do the trick.

```
find / -name myfile 2>/dev/null
```

That'll throw away any error messages from the command.

Alternatively you could just use ```
locate myfile
```

---

### Post by abcuser on 2007-10-31
@spec-chum: thanks, both commands work well.

If I understand correctly if multiple files exists with same name then locate will return only first path of file. Find command will return all paths.

---

