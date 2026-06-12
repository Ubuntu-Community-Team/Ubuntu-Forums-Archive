---
title: "Num Lock query"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-01-25
Each time I boot the num lock is off.

There doesn't seem to be anything in BIOS to set this as ON.

I think there must be something in WindowsXP as it was always locked when Windows loads.

Is there anyway in 6.06 where I can num lock on when booted?

Thanks
David

---

### Post by hyper_ch on 2007-01-25
You could try to install this package:

numlockx

---

### Post by r4ik on 2007-01-25
Turn numlock on and then paste these two commands into the terminal:
Code:

wget -c [http://ubuntu.cs.utah.edu/ubuntu/pool/universe/n/numlockx/numlockx_1.1-5_i386.deb](http://ubuntu.cs.utah.edu/ubuntu/pool/universe/n/numlockx/numlockx_1.1-5_i386.deb) sudo dpkg -i numlockx_1.1-5_i386.deb

That's the quick and dirty. If you want to understand a bit more about installing software, read these links:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

credits Aysiu

---

