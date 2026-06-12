---
title: "su to change menu.lst (read onlly)?"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by asinsh on 2006-01-31
I'm using kubuntu and I've been trying to change boot/grub.menu.lst in Kate, but I find that I cannot save the change because it is read only.  So I tried to split Kate to include terminal mode and use su, but when I give it my password the authentication fails.  Funny thing is that the password works fine for sudo.  Any ideas about how I can get su to work (or how I can otherwise change menu.lst and save the changes)?

Thanks.

---

### Post by asinsh on 2006-01-31
I think I've got it figured out.  I needed to chmod 777 to open it up.  Then I was able to save the change.  Once I did that I did a chmod 644 to change it back to read only for anyone other than the owner (root).  Did I close it down correctly?

---

### Post by aysiu on 2006-02-01
That's not really how you're supposed to do it. It's read-only for a reason--because it's a critical system file.

The "proper" way to edit it is ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo kwrite /boot/grub/menu.lst
``` or Alt-F2 ```
kdesu konqueror
```

---

