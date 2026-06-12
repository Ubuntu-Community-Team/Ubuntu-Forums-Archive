---
title: "MythTV Wake Permissions Problem"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by Pinckman1360 on 2007-11-17
Hello Everyone,

I am new to linux and have MythTv up and ruuning, but I am having a hard time getting the ACPI Shutdown/Wakeup procedure to work.  I followed the instructions MythTV ACPI Shutdown/Wakeup given at Ubuntu community..  Everything worked successfully up to step 2.6 "Another Test", where I enter "mythbackend &".  I get the following:

john@john-htpc:~$ 2007-11-17 13:54:56.222 Using runtime prefix = /usr
2007-11-17 13:54:56.231 New DB connection, total: 1
2007-11-17 13:54:56.235 Connected to database 'mythconverg' at host: localhost
2007-11-17 13:54:56.237 Current Schema Version: 1160
Starting up as the master server.
2007-11-17 13:54:56.246 New DB connection, total: 2
2007-11-17 13:54:56.246 Connected to database 'mythconverg' at host: localhost
2007-11-17 13:54:56.248 EITHelper: localtime offset -5:00:00 
2007-11-17 13:54:56.251 New DB connection, total: 3
2007-11-17 13:54:56.251 Connected to database 'mythconverg' at host: localhost
2007-11-17 13:54:56.570 New DB scheduler connection
2007-11-17 13:54:56.570 Connected to database 'mythconverg' at host: localhost
QServerSocket: failed to bind or listen to the socket
2007-11-17 13:54:56.577 MediaServer::HttpServer Create Error
2007-11-17 13:54:56.577 Main::Registering HttpStatus Extension
2007-11-17 13:54:56.578 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-11-17 13:54:56.578 Enabled verbose msgs:  important general
/var/lib/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!


Your help is greatly appreciated.

---

