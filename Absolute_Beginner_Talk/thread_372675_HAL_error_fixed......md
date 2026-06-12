---
title: "HAL error fixed....."
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by ginnie6 on 2007-02-28
had my first "problem" with ubuntu recently. For some reason I kept getting a HAL error on startup. Did some searching on the forums, turned the auto login off and the error is gone!

---

### Post by martin_legion on 2007-03-04
I have the same problem, except that some times I still get that error message, and since I started getting that error my usbdisk is mounted read-only so I must listen to the same songs in my mp3 player forever :S
I never changed anything in fstab or anything like that.
I reinstalled HAL but the error message keeps showing up.
Any ideas?
Thanks

---

### Post by shirilover on 2007-03-04
if necessary, you can log in to a tty terminal (Ctrl+Alt+[F1-F6]) and

```
sudo /etc/init.d/gdm stop  or kdm if KDE
sudo /etc/init.d/dbus restart
sudo /etc/init.d/gdm start
```

---

### Post by kelbizzle on 2007-03-04
I had the same issue.  I read somewhere on the internet that it may have something to do with Samba mounts in the fstab file or automatic login of gdm. The article said to use a timed login in conjunction with the automatic login so it will give everything a chance to initialize. I did that and I havn't seen it since. I'll try and find the link....found it. [http://beans.seartipy.com/2006/11/25/ubuntu-610-annoyance-failed-to-initialize-hal-error/](http://beans.seartipy.com/2006/11/25/ubuntu-610-annoyance-failed-to-initialize-hal-error/)

---

