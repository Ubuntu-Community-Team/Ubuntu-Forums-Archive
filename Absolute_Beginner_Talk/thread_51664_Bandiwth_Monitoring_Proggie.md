---
title: "Bandiwth Monitoring Proggie?"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by ozzie123 on 2005-07-24
Hello,

Is there any bandwith monitoring programs for Ubuntu (like DU Meter and the likes)?

Thanks
PS: I don't know wether this entry should be made under Application Support or ABT, but feel free to move it to the appropriate forum...

---

### Post by crmanski on 2005-07-24
I really like ntop for this. 
sudo apt-get install ntop
(I think you need universe repositories enabled)

If everything installs well then point your web browser to [http://127.0.0.1:3000](http://127.0.0.1:3000)

[QUOTE=ozzie123]Hello,

Is there any bandwith monitoring programs for Ubuntu (like DU Meter and the likes)?

Thanks
PS: I don't know wether this entry should be made under Application Support or ABT, but feel free to move it to the appropriate forum...[/QUOTE]

---

### Post by ozzie123 on 2005-07-24
I've already installed it and run it via the console/terminal but it returns this error:

Mon Jul 25 08:29:26 2005  ntop will be started as user nobody
Mon Jul 25 08:29:26 2005  ntop v.3.0 SourceForge .tgz MT (SSL)
Mon Jul 25 08:29:26 2005  Configured on Mar 24 2005  3:56:53, built on Mar 24 2005 03:57:09.
Mon Jul 25 08:29:26 2005  Copyright 1998-2004 by Luca Deri <deri@ntop.org>
Mon Jul 25 08:29:26 2005  Get the freshest ntop from [http://www.ntop.org/](http://www.ntop.org/)
Mon Jul 25 08:29:26 2005  Initializing ntop
Mon Jul 25 08:29:26 2005  Checking eth0 for additional devices
Mon Jul 25 08:29:26 2005  Resetting traffic statistics for device eth0
Mon Jul 25 08:29:26 2005  DLT: Device 0 [eth0] is 1, mtu 1514, header 14
Mon Jul 25 08:29:26 2005  Initializing gdbm databases
Mon Jul 25 08:29:26 2005  Now running as requested user 'nobody' (65534:65534)
Mon Jul 25 08:29:26 2005  **FATAL_ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Mon Jul 25 08:29:26 2005  1. Is another instance of ntop running?
Mon Jul 25 08:29:26 2005  2. Make sure that the use you specified can write in the target directory

Which part should I fix?

---

### Post by ozzie123 on 2005-07-24
Oops, I think I get where I was wrong...

I think I should login as root user

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=ozzie123]Oops, I think I get where I was wrong...

I think I should login as root user[/QUOTE]

Or use "sudo" before the command.

---

### Post by ubuntp on 2005-07-25
iptraf

---

### Post by crmanski on 2005-07-25
It has been a while since I set this up but I am pretty sure that from a root terminal I set the password as described in the Debian Readme...
"At installation you may need to set the administration password. You do
that by running ntop with the option -A (or --set-admin-password). It
will prompt you for the password and then exit. Now start the ntop
daemon."

I do not run the program as root.  I have a user on my system called simply "ntop" and I run it at startup with this...
```

ntop -u ntop -d

```
Since in the previous post you were running ntop as nobody and you got the error..
"**FATAL_ERROR** ....open of /var/lib/ntop/prefsCache.db failed"
It means that the nobody account does not have read/write permissions to "/var/lib/ntop/prefsCache.db"

---

