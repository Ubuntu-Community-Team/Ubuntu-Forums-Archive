---
title: "Ubuntu equivalent to Windows Services?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2006-12-16
Can someone please tell me what the equivalent to windows services are (i.e. I would like to know which file I can modify to add/prevent services/scripts at bootup.)

Thanks a lot.

-J

---

### Post by benuski on 2006-12-16
One place is if you go to System->Administration-> Services, there's a list of programs you can turn on or off at startup.  Also, if you go to System->Preferences->Sessions you can add your own items to startup if they aren't on the the Services menu

---

### Post by JohnnyAvocado on 2006-12-16
Sorry, my bad. I should have said I was running the server edition (i.e. no GUI.) Thanks again.

---

### Post by az on 2006-12-16
Look in /etc/init.d

and read up about runlevels:

man init

But what exactly do you want to do?

---

### Post by xpod on 2006-12-16
Could always install BootUpManager(BUM) if you want  an easy graphical way to keep an eye on things?:D

EDIToh,,,,server edition

---

### Post by revertex on 2007-01-08
sysv-rc-conf, sysvconfig or rcconf (or both :)), it curses based, you can even use to manage a headless server via ssh.
i think that is most reliable use these tools to get the service status,
 then use /etc/init.d/SERVICENAME to start/stop/restart/reload and update-rc.d to add or remove services.

example, to stop samba:
```
/etc/init.d/samba stop
```

or to add or remove a service

```
update-rc.d SERVICE-NAME defaults
```
```
update-rc.d SERVICE-NAME remove
```

GUI even fail for admin tasks, MS Windows is the proof. 

cheers

---

