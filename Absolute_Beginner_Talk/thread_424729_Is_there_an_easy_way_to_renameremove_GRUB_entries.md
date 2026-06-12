---
title: "Is there an easy way to rename/remove GRUB entries?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-04-27
Just Curious, I just wish to rename

Vista/Longhorn (restored) to Vista and get rid of

Windows XP embedded (because that's Dell's MediaDirect, and CANNOT boot from Grub)

Thanks all!

---

### Post by gohanssjn on 2007-04-27
Well, I found menu.lst, so I guess the real question is how can I save my edits when it says read only?

---

### Post by Bachstelze on 2007-04-27
You need to edit the file as root :

```
sudo nano -w /boot/grub/menu.lst
```

---

### Post by aysiu on 2007-04-27
This will help you edit the file:
[http://www.psychocats.net/ubuntu/permissions#gui](http://www.psychocats.net/ubuntu/permissions#gui)

---

### Post by gohanssjn on 2007-04-27
You all are the best, thanks :D

---

