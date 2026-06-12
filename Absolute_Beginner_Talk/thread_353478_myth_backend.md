---
title: "myth backend"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-02-04
After  6 long hours of trial I have reached a poit where the only error I get is as follows.

Could not connect to the master backend server - - is it running? Is the IP address
set for it in the setup program.

I have checked everywhere I can figure but am gunshy after spending a few days getting
this far.

fenian  where are yoooo
Your guide almost worked. how about a clue

---

### Post by ifross on 2007-02-04
whenever that happens to me i do a 
```
sudo /etc/init.d/mythtv-backend restart
```

but im not sure whether that will do anything

---

### Post by squrl on 2007-02-04
I tried that but this is a first time run and it didn't help. I even did a reboot. The backend is running but the frontend cant find it.

---

### Post by fenian on 2007-02-05
It could be a permissions problem.If you didn't change the default directory for saving recordings it would be be /var/lib/mythtv ,if you did change the directory to hold recordings change /var/lib/mythtv to the appropriate path in the following commands...

> sudo chown mythtv.mythtv /var/lib/mythtv
sudo chmod u=rwx,g=rwxs,o=rx /var/lib/mythtv


---

