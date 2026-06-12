---
title: "nomachines fails to connect to X"
date: 2010-02-17
forum: Apple Hardware Users
---

### Post by bluethundr on 2010-02-17
Hello,

 I am using the nomachines client on my Mac OS X 10.6.2 "Snow Leopard' laptop. At the moment I am trying to connect the nomachines client to a centOS AWS instance and plan to tackle my debian/ubuntu AWS instances if/when I solve this problem.

 I am able to connect to the AWS user account I setup with nxserver --useradd user --system

 But as soon as it logs in it is not able to connect to the X windowing system.. I have tried both KDE and GNOME with exactly the same result

```


NXPROXY - Version 3.4.0

Copyright (C) 2001, 2007 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '1259'.
Session: Starting session at 'Wed Feb 17 21:48:28 2010'.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/131072KB/131072KB.
Info: Using pack method 'adaptive-7' with session 'gnome'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Using ZLIB data compression 1/1/32.
Info: Not using ZLIB stream compression.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display '/tmp/launch-744yHZ/:0'.
Info: Listening to font server connections on port '11007'.
Session: Session started at 'Wed Feb 17 21:48:28 2010'.
Info: Established X server connection.
Info: Using shared memory parameters 1/4096K.
Session: Terminating session at 'Wed Feb 17 21:48:32 2010'.
Session: Session terminated at 'Wed Feb 17 21:48:32 2010'.

```

---

### Post by 0x656b694d on 2010-03-17
Hi bluethundr,
have you fixed the issue yet?

---

