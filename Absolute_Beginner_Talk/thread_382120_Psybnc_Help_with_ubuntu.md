---
title: "Psybnc Help with ubuntu"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by krunk on 2007-03-11
Hi, im trying to compile a psybnc on ubuntu. make menuconfig gives me an error.. "error: label at end of compound statement". I tried manually editing the config with pico, but when i tried make I got the same error. Can anyone help me resolve this problem? Thanks!

---

### Post by krunk on 2007-03-11
well i managed to get psybnc compiled and running..

Listening on: 0.0.0.0 port 69666
psyBNC2.3.2-7-cBtITLdDMSoNp started (PID 10049)


I tried connecting to my ip address port 69666 with xchat but the connection was refused.. could ubuntu be blocking this port? is there any way i can open this port?

---

### Post by madmonk3y on 2007-06-12
Use an unused port between 1024 and 65535.  Your port is beyond the range of valid ports.

[http://ubuntuforums.org/showpost.php?p=2829953&postcount=1](http://ubuntuforums.org/showpost.php?p=2829953&postcount=1)

Try the above link.  If you still want to install PsyBNC knowing that and why it won't work correctly, here's the packages you need to be able to make menuconfig and have the compile complete (with warnings and future instability):

[http://ubuntuforums.org/showpost.php?p=2830116&postcount=5](http://ubuntuforums.org/showpost.php?p=2830116&postcount=5)

---

