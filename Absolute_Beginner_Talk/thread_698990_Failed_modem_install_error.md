---
title: "Failed modem install error"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by RoBo5050 on 2008-02-16
Hello forum members,
 I was trying to configurel a lucent modem driver for linux today,and got the following error after typing a different command than the normal "./configure:

rom@rom-desktop:~/Desktop/agrsm$ auto-apt run ./configure
Entering auto-apt mode: ./configure
Exit the command to leave auto-apt mode.
E: Exec ./configure failed, auto-apt failed
rom@rom-desktop:~/Desktop/agrsm$

Does anyone know what went wrong with this configure command???? :confused:

Thanks in advance for the reply!!

---

### Post by ashmew2 on 2008-02-17
Have you tried running only ./configure ? That may help to diagnose...

---

### Post by RoBo5050 on 2008-02-18
Hello forum members,
   I have tried the ./configure command,but have only gotten that the command was invalid,or couldn't get locate the command error!

I think I might re-install Ubuntu 7.10 to see if it installs the modem
then-I had a different modem on the mobo Ubuntu was first installed on;hopefully the modem driver will be installed when I re-install!!

---

### Post by spiderbatdad on 2008-02-18
Many modems have two modes of operation...data mode and modem mode. You may need to do a little research on your modem to find out if this is the case. The ./connect command would not work if the modem is not in modem mode. By default, the device probably mounts in data mode. Running fdisk -l while the modem is plugged in might should you an extra storage volume...that would be the modem in data mode.

---

