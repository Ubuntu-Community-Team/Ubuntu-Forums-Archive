---
title: "Jack on G5 PPC"
date: 2010-01-22
forum: Apple Hardware Users
---

### Post by mwille14 on 2010-01-22
Please can someone help with this or share the settings they have. At the moment i cannot connect to the server and get the following message:

23:52:59.516 Patchbay deactivated.
23:52:59.685 Statistics reset.
23:52:59.839 Startup script...
23:52:59.841 artsshell -q terminate
23:52:59.888 ALSA connection graph change.
sh: artsshell: not found
23:53:00.981 Startup script terminated with exit status=32512.
23:53:00.983 JACK is starting...
23:53:00.984 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p256 -n2 -m
23:53:01.076 JACK was started with PID=4752.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -134434288, from thread -134434288] (1: Operation not permitted)
cannot create engine
23:53:01.163 JACK was stopped successfully.
23:53:01.165 Post-shutdown script...
23:53:01.166 killall jackd
23:53:01.220 ALSA connection change.
jackd: no process killed
23:53:01.581 Post-shutdown script terminated with exit status=256.
23:53:03.231 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by linuxopjemac on 2010-01-23
Run this command:
```

sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf
```

Logout/in. Start JACK.

see [here]("http://ubuntuforums.org/showthread.php?t=453486")

---

