---
title: "pvr-150 lirc on 7.10 please help a nOOb"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Newbentu on 2007-10-27
I've been tryin to do this on my own for 3 days.  I give up.  Please help.  I really have no clue what the following means, but hopefully someone can help me correct it.

aaron@blackbox:~$ irw
connect: Connection refused
aaron@blackbox:~$ dmesg | grep -i lirc
[   74.205754] lirc_dev: IR Remote Control driver registered, at major 61 
aaron@blackbox:~$ 
aaron@blackbox:~$ sudo lircd -n
lircd-0.8.2[6396]: lircd(userspace) ready
lircd-0.8.2[6396]: accepted new client on /dev/lircd
lircd-0.8.2[6396]: could not get file information for /dev/lirc
lircd-0.8.2[6396]: default_init(): No such file or directory
lircd-0.8.2[6396]: caught signal
Terminated
aaron@blackbox:~$

---

### Post by Newbentu on 2007-10-27
I'm pretty sure It says I need to add it to my devices folder, but how now?

---

### Post by Newbentu on 2007-10-27
I'm also getting this response.  Don't know if it helps.

aaron@blackbox:~$ depmod -ae
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
aaron@blackbox:~$ modprobe lirc_i2c
aaron@blackbox:~$ chmod 666 /dev/lircd
chmod: changing permissions of `/dev/lircd': Operation not permitted
aaron@blackbox:~$ lircd
lircd: can't open or create /var/run/lircd.pid
lircd: Permission denied
aaron@blackbox:~$ irw

---

### Post by loctones on 2007-10-29
I was getting the same problems trying to run irw.  It seems my install set up /dev/lircd, but not /dev/lirc0.  Using "sudo modprobe lirc_i2c" created /dev/lirc0, and allowed me to use irw.

---

### Post by Eddie002Fast on 2007-10-29
how do i post jpg pics to a thread or post on a forum?  :D

---

