---
title: "Volume keys not working`"
date: 2009-02-04
forum: Apple Hardware Users
---

### Post by RobSoko315 on 2009-02-04
Hey, 

I'm running intrepid on a MacBook Pro 3.1 (Santa Rosa).  With Kernal 2.6.27-11.

The function keys that control volume isn't working.  The weird part is when I press the keys, I see the Mac-like volume display go up and down, but the volume itself doesn't change.

I ran the command "alsamixer", and it is set at 100%.

Thanks for any help

Rob.

---

### Post by cyberdork33 on 2009-02-04
try starting alsamixer like this:
```
alsamixer -c 0
```

---

