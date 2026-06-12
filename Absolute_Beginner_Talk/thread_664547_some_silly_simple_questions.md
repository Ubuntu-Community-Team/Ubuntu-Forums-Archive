---
title: "some silly simple questions"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-11
What do those things mean?
1.whlie i was using the live install i checked the auth.log from curiosity and i saw this: 
"...ubuntu gdm(...):pam_env(gdm-autologin:sected): unable to open file:/etc/default/locale:no such file or directory


2.During live install after coping the files the ubuntu scans on the mirror and actually updates 
the system the same time or waits until reboot....?

3.every time i reboot i have a message saying somewhere ...var/lib/..manufacturer:no such file or directory

and how can i see my active connections through terminal?

---

### Post by DavidTangye on 2008-01-11
1. The live install has autologged you into ubutu as a user called 'ubuntu', hence the 'autologin' message. At this stage you have not selected your country, so it does not have a 'locale'. It will fall back to using the default called 'C'.

2. Dunno. Open console 1 or 2 and check what its doing. (Ctl-Alt-1, Ctl-Alt-2).

3. Dunno.

What do you mean by 'active connections'?

---

### Post by someoneouthere on 2008-01-11
i mean when im connected somewhere how can i check it out in rel time?
and if there isn't already  how to create an automated log file for the ip-adresses?

---

### Post by OffAxis on 2008-01-11
```
netstat
```

will show your connections. There are a lot of different options for it, you should read up on the man page
```
man netstat
```

**```
netstat -pant
```**

is probably want you want.

---

