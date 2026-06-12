---
title: "cannot unmount volume"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Baufo on 2007-09-15
Hello everyone!

I have successfully used the method described at [http://ubuntuforums.org/showthread.php?t=546252](http://ubuntuforums.org/showthread.php?t=546252) to get write permission on my Windows partition.
When I am, however, trying to unmount this volume again it complains that only the root could do that. How can I perform this action as root?

Thank you in advance,
Baufo

---

### Post by pay on 2007-09-15
I think its ```
sudo umount /dev/<device>
```

---

### Post by Baufo on 2007-09-15
Thanks you. But now I have a really weird problem. When I have entered this command it asks me for my password which I am unable to enter because it won't let me type.

EDIT: My bad, I just found out it just isn't displaying what I type, it working fine now.

---

