---
title: "Erratically losing network connectivity (with logs!)"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-12-27
Apparently, samba resets itself every hour. I guess that's normal. What doesn't seem to be normal is this sample from /var/log/syslog
 
```
Dec 27 08:00:01 white /USR/SBIN/CRON[6400]: (root) CMD (/etc/webmin/bandwidth/rotate.pl)
Dec 27 08:00:02 white exiting on signal 15
Dec 27 08:00:02 white syslogd 1.4.1#21ubuntu3: restart.
Dec 27 08:09:01 white /USR/SBIN/CRON[6428]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 27 08:15:56 white dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Dec 27 08:15:56 white dhclient: DHCPACK from 192.168.1.1
Dec 27 08:15:56 white NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
Dec 27 08:15:56 white dhclient: bound to 192.168.1.146 -- renewal in 34144 seconds.
Dec 27 08:17:01 white /USR/SBIN/CRON[6449]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 27 08:26:22 white winbindd[5584]: [2007/12/27 08:26:22, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 08:26:22 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 08:26:22 white smbd[6451]: [2007/12/27 08:26:22, 0] auth/auth_util.c:create_builtin_administrators(792) 
Dec 27 08:26:22 white smbd[6451]:   create_builtin_administrators: Failed to create Administrators 
Dec 27 08:26:22 white winbindd[5584]: [2007/12/27 08:26:22, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 08:26:22 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 08:26:22 white smbd[6451]: [2007/12/27 08:26:22, 0] auth/auth_util.c:create_builtin_users(758) 
Dec 27 08:26:22 white smbd[6451]:   create_builtin_users: Failed to create Users 
Dec 27 08:26:22 white winbindd[4840]: [2007/12/27 08:26:22, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 08:26:22 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Dec 27 08:26:22 white winbindd[4840]: [2007/12/27 08:26:22, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 08:26:22 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Dec 27 08:39:01 white /USR/SBIN/CRON[6453]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 27 08:58:22 white winbindd[5584]: [2007/12/27 08:58:22, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 08:58:22 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 08:58:22 white smbd[6503]: [2007/12/27 08:58:22, 0] auth/auth_util.c:create_builtin_administrators(792) 
Dec 27 08:58:22 white smbd[6503]:   create_builtin_administrators: Failed to create Administrators 
Dec 27 08:58:22 white winbindd[5584]: [2007/12/27 08:58:22, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 08:58:22 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 08:58:22 white smbd[6503]: [2007/12/27 08:58:22, 0] auth/auth_util.c:create_builtin_users(758) 
Dec 27 08:58:22 white smbd[6503]:   create_builtin_users: Failed to create Users 
Dec 27 08:58:22 white winbindd[4840]: [2007/12/27 08:58:22, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 08:58:23 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Dec 27 08:58:23 white winbindd[4840]: [2007/12/27 08:58:23, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 08:58:23 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 

```
 
That's a sample from 8:00 this morning.  I could post pretty much the same thing from any hour of the day.  
 
Sometimes there isn't any problem... the computer "stays on" the network. Othertimes, and maybe it would fix itself if I waited an hour, it's inaccessible. I run it headless. It does nothing but hold a bunch of hard drives that are mapped/mounted on other computers and xboxes throughout the house. I never had this problem in feisty. Any suggestions?
 
Thanks in advance.

---

### Post by randomjohn on 2007-12-27
The 2:00 refresh had even more activity:
 
```
Dec 27 14:00:01 white /USR/SBIN/CRON[6793]: (root) CMD (/etc/webmin/bandwidth/rotate.pl)
Dec 27 14:00:02 white exiting on signal 15
Dec 27 14:00:02 white syslogd 1.4.1#21ubuntu3: restart.
Dec 27 14:00:38 white winbindd[5584]: [2007/12/27 14:00:38, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:00:38 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:00:38 white smbd[6820]: [2007/12/27 14:00:38, 0] auth/auth_util.c:create_builtin_administrators(792) 
Dec 27 14:00:38 white smbd[6820]:   create_builtin_administrators: Failed to create Administrators 
Dec 27 14:00:38 white winbindd[5584]: [2007/12/27 14:00:38, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:00:38 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:00:38 white smbd[6820]: [2007/12/27 14:00:38, 0] auth/auth_util.c:create_builtin_users(758) 
Dec 27 14:00:38 white smbd[6820]:   create_builtin_users: Failed to create Users 
Dec 27 14:00:38 white winbindd[4840]: [2007/12/27 14:00:38, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:00:38 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Dec 27 14:00:38 white winbindd[4840]: [2007/12/27 14:00:38, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:00:38 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Dec 27 14:08:54 white winbindd[5584]: [2007/12/27 14:08:54, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:08:54 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:08:54 white smbd[6821]: [2007/12/27 14:08:54, 0] auth/auth_util.c:create_builtin_administrators(792) 
Dec 27 14:08:54 white smbd[6821]:   create_builtin_administrators: Failed to create Administrators 
Dec 27 14:08:54 white winbindd[5584]: [2007/12/27 14:08:54, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:08:54 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:08:54 white smbd[6821]: [2007/12/27 14:08:54, 0] auth/auth_util.c:create_builtin_users(758) 
Dec 27 14:08:54 white smbd[6821]:   create_builtin_users: Failed to create Users 
Dec 27 14:08:54 white winbindd[4840]: [2007/12/27 14:08:54, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:08:54 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Dec 27 14:08:54 white winbindd[4840]: [2007/12/27 14:08:54, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:08:54 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Dec 27 14:09:01 white /USR/SBIN/CRON[6823]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 27 14:12:39 white winbindd[5584]: [2007/12/27 14:12:39, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:12:39 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:12:39 white smbd[6829]: [2007/12/27 14:12:39, 0] auth/auth_util.c:create_builtin_administrators(792) 
Dec 27 14:12:39 white smbd[6829]:   create_builtin_administrators: Failed to create Administrators 
Dec 27 14:12:39 white winbindd[5584]: [2007/12/27 14:12:39, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:12:39 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:12:39 white smbd[6829]: [2007/12/27 14:12:39, 0] auth/auth_util.c:create_builtin_users(758) 
Dec 27 14:12:39 white smbd[6829]:   create_builtin_users: Failed to create Users 
Dec 27 14:12:39 white winbindd[4840]: [2007/12/27 14:12:39, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:12:39 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Dec 27 14:12:39 white winbindd[4840]: [2007/12/27 14:12:39, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:12:39 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Dec 27 14:17:01 white /USR/SBIN/CRON[6831]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 27 14:18:30 white winbindd[5584]: [2007/12/27 14:18:30, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:18:30 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:18:30 white smbd[6833]: [2007/12/27 14:18:30, 0] auth/auth_util.c:create_builtin_administrators(792) 
Dec 27 14:18:30 white smbd[6833]:   create_builtin_administrators: Failed to create Administrators 
Dec 27 14:18:30 white winbindd[5584]: [2007/12/27 14:18:30, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Dec 27 14:18:30 white winbindd[5584]:   ERROR: Initialization failed for alloc backend, deferred! 
Dec 27 14:18:30 white smbd[6833]: [2007/12/27 14:18:30, 0] auth/auth_util.c:create_builtin_users(758) 
Dec 27 14:18:30 white smbd[6833]:   create_builtin_users: Failed to create Users 
Dec 27 14:18:30 white winbindd[4840]: [2007/12/27 14:18:30, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:18:30 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Dec 27 14:18:30 white winbindd[4840]: [2007/12/27 14:18:30, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Dec 27 14:18:30 white winbindd[4840]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 

```

---

