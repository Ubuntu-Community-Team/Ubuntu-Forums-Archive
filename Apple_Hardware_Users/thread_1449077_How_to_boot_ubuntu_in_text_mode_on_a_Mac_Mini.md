---
title: "How to boot ubuntu in text mode on a Mac Mini"
date: 2010-04-07
forum: Apple Hardware Users
---

### Post by lock55 on 2010-04-07
I have an Intel MacMini (Macmini2,1) running with Ubuntu 8.04  without a hitch (used rEFIt 0.13 and erased the OS X partition).

I want to make the machine start in text mode instead of X.

Any help would be appreciated.

---

### Post by linuxopjemac on 2010-04-07
**Step 1**
Just edit /etc/default/grub with your favourite editor:

    ```
sudo gedit /etc/default/grub
```

find out this line:

    ```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

change it to:

    ```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash text”
```

**Step 2**
Update grub and done!

    ```
sudo update-grub
```

---

