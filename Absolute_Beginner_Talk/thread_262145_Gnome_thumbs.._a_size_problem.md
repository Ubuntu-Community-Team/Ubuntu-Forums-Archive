---
title: "Gnome thumbs.. a size problem"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by nalinde on 2006-09-21
Ok.. recently noticed that my Ubuntu system got bigger and bigger (size) and started to clean up my system. You would be surprised how  much free disk space you can get by empty your root trash :p .

Anyway... was playing around in my home catalogue and fond the .thumbnails directory. Found about 10 000 thumbs in there taking up space. The funny thing is that i found thumbs in there from pictures that I've deleted Loooong time ago.

So to the Question. Is there any way to get gnome delete the thumbs as the pictures is deleted  in my .trash?

Cheers Martin

---

### Post by kidders on 2006-09-21
Hi there,

What's your "root trash"?

Those thumbnail caches are only generated for performance reasons ... you can turn it off altogether if you want to, I presume. Another option might be to use **cron** to empty them on, say, a weekly basis.

**Edit:** If you want to delete them all manually, try **sudo rm -Rf /home/*/.thumbnails**

---

