---
title: "Ubuntu automatically changes permissions on startup?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by drazgo on 2008-01-04
hi, 

I'm having issues with permissions i am trying to set on my ubuntu 7.10 system. I changed the perms on directory /var/run to 777 and everything works just fine. But when i restart my machine, all permissions I have set are gone and the default perms are back...

any ideas which may cause this?

thanks in advance!

---

### Post by Sukarn on 2008-01-04
I don't know what's causing it, I'm not knowledgeable enough for that, but a dirty hack you can try is to set up a script that automatically changes the permission at boot time.

---

### Post by drazgo on 2008-01-04
any chance of telling me where i can find such script? :P

---

### Post by kpkeerthi on 2008-01-04
Please understand the implications of changing permissions on such system folder.
From [http://www.pathname.com/fhs/2.2/fhs-5.13.html](http://www.pathname.com/fhs/2.2/fhs-5.13.html)
> 
This directory contains system information data describing the system since it was booted. Files under this directory must be cleared (removed or truncated as appropriate) at the beginning of the boot process. Programs may have a subdirectory of /var/run; this is encouraged for programs that use more than one run-time file.

/var/run should be unwritable for unprivileged users (root or users running daemons); it is a major security problem if any user can write in this directory. Process identifier (PID) files, which were originally placed in /etc, must be placed in /var/run. The naming convention for PID files is <program-name>.pid. For example, the crond PID file is named /var/run/crond.pid.


Why do want to change permission of /var/run? Perhaps there is a cleaner way to achieve what you want.

---

### Post by drazgo on 2008-01-04
well, i keep getting this error message when i want to join a domain: 

> ave@ave-laptop:~$ net ads join
[2008/01/04 10:25:25, 0] libads/kerberos.c:create_local_private_krb5_conf_for_domain(641)
  create_local_private_krb5_conf_for_domain: smb_mkstemp failed, for file /var/run/samba/smb_tmp_krb5.4z3gbM. Errno Permission denied
[2008/01/04 10:25:25, 0] libads/kerberos.c:create_local_private_krb5_conf_for_domain(647)
  create_local_private_krb5_conf_for_domain: fchmod failed for /var/run/samba/smb_tmp_krb5.4z3gbM. Errno Bad file descriptor


everytime i wanna start my laptop, i want to be able to login using a domain username, but my pc just doesn't 'order' a kerberos ticket because of that problem...

---

### Post by drazgo on 2008-01-04
anyone?? :confused:

---

### Post by hyper_ch on 2008-01-04
well something's really wrong with your setup... but how to fix it? No clue...

---

