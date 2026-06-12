---
title: "Editting Grub after Dapper to Edgy Upgrade"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by dpar on 2007-02-01
I just Upgraded Dapper to Edgy, but now my Grub menu shows both Dapper and Edgy kernels. I would like to clean it up a bit to make it easier to read. Can I just comment out the kernels that I don't want displayed in menu.lst, with no terrible side effects????[-o< 

Thanks for any help in advance.
Dave

---

### Post by taurus on 2007-02-01
Shouldn't be a problem at all.  Just place a # in front of the line in /boot/grub/menu.lst that you want to comment out.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by dpar on 2007-02-01
Thanks Taurus, I thought it might be ok, but it is easier to do it right than to try and fix a screwup.....lol

Thanks again

---

