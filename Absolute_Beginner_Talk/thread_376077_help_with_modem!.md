---
title: "help with modem!"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by kyusstool on 2007-03-04
right i am a complete beginner and know of a few problems with the speedtouch 330 modem.i cant connect and have tried the speedtouchconf.sh thing but cant get it to work.if anyone could talk me through it i woulb be very grateful.
i am using ubuntu 6.06lts for 64 bit pc!

---

### Post by chggr on 2007-03-04
speedtouchconf.sh is a shell script and you need to run it using the Terminal.
Open a terminal, use the command cd to get inside the folder where speedtouchconf resides and type in the following commands:

1) chmod 777 speedtouchconf.sh
(this gives everybody permissions to execute, write and read the file)

2) ./speedtouchconf.sh
(this runs the shell script)

---

