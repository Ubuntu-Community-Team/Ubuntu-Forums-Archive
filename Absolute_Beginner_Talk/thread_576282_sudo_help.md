---
title: "sudo help"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2007-10-15
i will be installing a computer into my car next week that has a touch screen and to calibrate it i have to sudo su change directories and run the calibration program.  what i am looking for is away to always have root permission.  I've fooled around for awhile and was unsuccessful.  Input is aways wanted thanks.

---

### Post by startherepodcast on 2007-10-15
First set the root password:

```
sudo passwd root
```

Then you can login with the user root and the password you just set.

---

### Post by endlessurf on 2007-10-15
thanks for the reply that was what i was looking for.  I have another question along the same lines,  I have one other user set up besides root, and of course that is where all my media is at.  when i look on as root, how to i access all of my other media in the other login name

---

### Post by PacketCollision on 2007-10-15
Navigate to /home/*username*

---

