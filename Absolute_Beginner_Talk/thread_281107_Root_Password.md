---
title: "Root Password?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Wizdancer on 2006-10-20
I will switch in a couple of months (when i get my new computer), and i heard somewhere that you dont create your root password during installation, is that correct?

Thanks in Advance 
-Wizdancer

---

### Post by taurus on 2006-10-20
That's correct.  If you need to run something that requires root, then you use the sudo...

```
sudo <command
```

---

### Post by ReaderRat on 2006-10-20
> **Wizdancer said:**
> I will switch in a couple of months (when i get my new computer), and i heard somewhere that you dont create your root password during installation, is that correct?
That is correct. If you want to see how that works, read this:
sudo - How it works
         [How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

### Post by aysiu on 2006-10-20
If you're a drag-and-drop sort, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by randomi on 2006-10-20
If you really want to create your own root password once the install is completed you can either

```
sudo passwd root
```

or use Users and Groups (gui app) which can be found under System -> Administration.

I would advise again logging in as root, as there's really no reason to in Ubuntu. The advancements they've made with sudo kills any reason to really need to log in as root. If you ever find a reason to the above is how you can set a root password. There is more that would have to be done to log into a desktop environment as root that you can find here on the forums.

---

