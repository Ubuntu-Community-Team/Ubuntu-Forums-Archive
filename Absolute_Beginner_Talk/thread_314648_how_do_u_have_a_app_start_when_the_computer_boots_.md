---
title: "how do u have a app start when the computer boots up before"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-12-07
i want to have the following app start when the computer finishes booting but before anyone logs in..

/home/john/desktop/app/./start

---

### Post by taurus on 2006-12-07
I guess you can create a symbolic link to /etc/init.d!

```
sudo ln -s  /home/john/desktop/app/program  /etc/init.d/program
```
p.s.  There is already a command called start (to start processes) so it's not a good idea to name your program start...

---

