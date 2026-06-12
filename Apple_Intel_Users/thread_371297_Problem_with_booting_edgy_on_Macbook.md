---
title: "Problem with booting edgy on Macbook"
date: 2007-02-26
forum: Apple Intel Users
---

### Post by hansoffate on 2007-02-26
I forgot to do this command:

To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)
N.B.: It will automatically be applied to the installed system so you won't have to enter it manually ever again!

When i installed edgy on my macbook. How do i fix this?

Thanks
-Hans

---

### Post by oskarloko on 2007-02-27
Just edit your boot config file with that option...

```
sudo gedit /boot/grub/menu.lst
```

or the lilo configuration file

Search your kernel line and add ```
lpj=8000000
``` at he end

---

### Post by cocoia on 2007-02-27
This shouldn't really be all that needed. I am running fine, even without noapic flags or this boot flag, I rarely have a panic on boot. Does this make problems for you, or do you just want to be on the safe side?

---

### Post by hansoffate on 2007-02-27
It has happened twice where it wouldn't boot out of 6 times.

As a side note, how do I get ubuntu-desktop installed?  sudo apt-get install ubuntu-desktop.  When i do that it doesn't install.  

Any ideas?
Thanks
-Hans

---

