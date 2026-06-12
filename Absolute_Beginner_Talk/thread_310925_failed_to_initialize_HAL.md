---
title: "failed to initialize HAL?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by FLCLFan on 2006-12-02
I have ubuntu 6.1 and Every time i start it up i get "Internal Error - failed to initialize HAL!" How do i fix this?

---

### Post by Ecthelion on 2006-12-02
Hi,

I've had the same problem and the only solution I found is a timed login.
Instead of letting your machine log in immediatly, choose to login only after 5 seconds.
Maybe not really a fix but this made the error go away and also some other network issue I had...

I hope this helps you too...

---

### Post by FLCLFan on 2006-12-02
That didn't work :( .Anyone else know what to do?

---

### Post by heggel on 2006-12-07
Hi.

Don't ask me why, but 

sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

did the trick for me.
([http://easylinuxguide.com/forum/index.php?topic=68.msg233](http://easylinuxguide.com/forum/index.php?topic=68.msg233)
and 
[https://launchpad.net/distros/ubuntu/+source/dbus/+bug/19577](https://launchpad.net/distros/ubuntu/+source/dbus/+bug/19577))

Ciao!

---

