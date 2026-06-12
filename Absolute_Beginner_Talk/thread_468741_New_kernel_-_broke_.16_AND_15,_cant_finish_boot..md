---
title: "New kernel - broke .16 AND 15, cant finish boot."
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by khardbored on 2007-06-09
So I updated to the latest kernel tonight and restarted as it asked me to. I noticed something was wrong when my custom splash screen had a bunch of missing text. The loading bar got about half way then it dropped me into a console and started going down the startup list. Then tried starting X, couldnt start x and now im just sitting at a login screen. The text before the login says stuff like
```
kinit name_to_dev_t(/dev/disk/by-uuid/numbers-letters)
```
Then it repeats this and ends with no resume image, doing normal boot.

So I notice that my previous kernel is no longer listed in grub, just the .15. So I try to boot it and it gives me the same problem. Erg. Thoughts?

---

