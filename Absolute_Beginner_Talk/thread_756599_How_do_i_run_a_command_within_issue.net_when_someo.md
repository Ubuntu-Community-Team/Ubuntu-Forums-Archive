---
title: "How do i run a command within issue.net when someone logs in via SSH?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Gizim on 2008-04-16
Like i want a few commands to run such as acpi -V and it is in issue.net but when i login it just says acpi -V it doesnt run the command. Also is there a way to turn off the login spam?

Linux yoshi 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

---

### Post by joshrobinson on 2008-04-16
```
sudo gedit /etc/motd
```

to change that login message stuff

---

### Post by Gizim on 2008-04-16
> **joshrobinson said:**
> ```
sudo gedit /etc/motd
```

to change that login message stuff

How about to make it run a command? still only says acpi -V doesnt really run it

---

### Post by joshrobinson on 2008-04-16
> **Gizim said:**
> How about to make it run a command? still only says acpi -V doesnt really run it

not sure on that one, i just answered the only part i knew sorry
are you using ssh to get into a laptop?

because i thought acpi -V displayed laptop battery info

---

### Post by Gizim on 2008-04-16
> **joshrobinson said:**
> not sure on that one, i just answered the only part i knew sorry
are you using ssh to get into a laptop?

because i thought acpi -V displayed laptop battery info

Yeah its a laptop i have a few things running on it plus its just me learning

---

### Post by Gizim on 2008-04-16
Found it

Added to /etc/profile

---

