---
title: "Permissions"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-10
Hi
I've just briefly wandered into Simply MEPIS (from Ubuntu Dapper) and find I'm unable to carry out a simple command which I had actioned with no problem yesterday through Ubuntu.
Here's the command:
```
sudo chroot /media/sdb7
```

and here's the resulting error message:

> chroot: cannot run command `/bin/bash': Permission denied

Note that the command were run from Root.

Anything obvious I'm overlooking?

Thanks
Paul

---

### Post by halfvolle melk on 2006-08-10
Why use sudo if you're root already?

---

### Post by PaulFXH on 2006-08-10
Hi
Thanks for the reply.
I used sudo simply because I generally copy&paste where possible and that's what was written.
However, I doubt if you are saying that using sudo actually CAUSED the problem?

Paul

---

### Post by MaximB on 2006-08-10
I don't think that sudo caused this
maybe you should look at the premmisions on sdb7 on both linuxes
maybe b/z you have to linuxes - there might be a problem with the premmisions.

---

### Post by moma on 2006-08-10
The partition may been mounted with **noexec** flag, so chroot is not allowed to run /bin/sh.

Do this first:
$ [COLOR="Green"]sudo mount -o defaults,remount,exec /media/sdb7[/COLOR]

Then 
$ [COLOR="Green"]sudo chroot /media/sdb7 /bin/bash -i [/COLOR]
the /bin/sh -i  is default IIRC.  Just press cntr+c if it complains about /dev/null.

---

### Post by PaulFXH on 2006-08-10
Thanks to everybody for the replies.
I followed moma's detailed remedy and everything went remarkably smoothly.
Many thanks for this and best wishes
Paul

---

