---
title: "proftpd startup"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by boga on 2007-02-27
Hi everyone!
I've installed and configured proftpd and it works fine if I start gproftpd and press "Activate". However I need it to start on system startup. Somewhere I've found a recommendation to place this:
```
sudo /etc/init.d/proftpd start
```
into System->Preferences->Sessions->Startup Programs
It does start proftpd, however the server responds with "login incorrect" on any login attempt. If I deactivate and activate it from gproftpd it works fine, if I deactivate it and run the line above from the terminal it starts producing the following messages:
```
 * Starting ftp server proftpd                                                  
 - IPv6 getaddrinfo 'boga.ttk.ru' error: Name or service not known

```
and once again refuses any login attempt. Tried with both ipv6 enabled and disabled with no difference. The proftpd is configured to run as standalone server. Really I'd like to run it and samba from inetd but I can't see any inetd in my system.

---

