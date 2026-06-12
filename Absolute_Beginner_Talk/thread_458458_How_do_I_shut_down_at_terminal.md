---
title: "How do I shut down at terminal?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by yeago on 2007-05-29
Disappointment number 1 of 500 with Ubuntu: How to get shutdown to shut down?

hey there, running Feisty server.

SUDO SHUTDOWN NOW stops a bunch of services, but then goes:

*Will now switch to single-user mode.
Give root password for maintenance (or type Control-D to continue): init rc1 main process (5033) killed by TERM signal

Typing Control+D then starts everything back up. (!?!?!??!?!)

---

### Post by floke on 2007-05-29
I think its sudo shutdown 0

---

### Post by Ek0nomik on 2007-05-29
```
sudo shutdown -r now
```

?

---

### Post by YoG%*@ on 2007-05-29
try
```

sudo shutdown -h now

```

EDIT: (the -r option reboots, -h really powers down the system... have a look at the man page for more info!)

---

### Post by Ek0nomik on 2007-05-29
> **mux said:**
> try
```

sudo shutdown -h now

```

EDIT: (the -r option reboots, -h really powers down the system... have a look at the man page for more info!)

Yep, my mistake.  I am so used to running -r, and posting on the forums on Windows at work doesn't help.  ;)

---

### Post by lambros on 2007-05-29
You could use
```
sudo poweroff
```
to power down the system.  Another useful command is
```
sudo reboot
```
to cause the system to shutdown then restart automatically.

Lambros

---

### Post by Swab on 2007-05-29
or... sudo poweroff

---

### Post by macjones on 2007-09-11
> **yeago said:**
> Disappointment number 1 of 500 with Ubuntu: How to get shutdown to shut down?

hey there, running Feisty server.

SUDO SHUTDOWN NOW stops a bunch of services, but then goes:

*Will now switch to single-user mode.
Give root password for maintenance (or type Control-D to continue): init rc1 main process (5033) killed by TERM signal

Typing Control+D then starts everything back up. (!?!?!??!?!)

-------------------

use 

shutdown -h now

---

