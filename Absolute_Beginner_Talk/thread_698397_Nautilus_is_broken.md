---
title: "Nautilus is broken"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by iancvt55 on 2008-02-16
Hi

I was trying to move a folder into /etc

somehow I messed up Nautilus and this is what I now get:

ian@vulcan607:~$ sudo nautilus
sudo: /etc/sudoers is mode 0666, should be 0440
ian@vulcan607:~$ gksudo nautilus
ian@vulcan607:~$ 

Help!

Thanks

Ian

---

### Post by drs305 on 2008-02-16
Restart and boot into recovery mode from the menu. Once you get to the prompt:
```
chmod 440 /etc/sudoers
shutdown -r now
```

That should change the permission back to what it should be.

---

### Post by iancvt55 on 2008-02-16
drs305

Thanks worked a treat. I have added it to my linux notes document which I still keep on Windows (for now).

---

