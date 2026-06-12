---
title: "Standby &amp; Hibernate from terminal?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-10-04
Is it possible to go into standby and/or hibernate from the terminal? I am using beryl and lose these options aswell as shutdown and reboot (using KDE) but I know how to do reboot and shutdown, just not standby and hibernate.

Calv

---

### Post by davmac on 2006-10-05
Don't know about standby but on my asus laptop I can hibernate with the command "sudo /etc/acpi/hibernate.sh".

EDIT: I notice in the /etc/acpi directory there is a "sleep.sh" script. Not tried it myself, but worth a go...

Hope this helps,

Dave Mac

---

### Post by xyz on 2006-10-05
I go to sleep with
```
 echo -n mem > /sys/power/state

```
as root on my Toshiba. I learned it from the links in my sig.

---

### Post by jastonas on 2008-05-25
Is there a similar command to "shutdown -h +*minutes" for standby or hibernation??

---

### Post by ChameleonDave on 2008-05-25
> **jastonas said:**
> Is there a similar command to "shutdown -h +*minutes" for standby or hibernation??

Well, you can use the "sleep" command (not to be confused with "sleep.sh" which refers to suspending to RAM) to delay anything.

```

sudo -s
sleep 10m ; /etc/acpi/sleep.sh
```

or 

```

sudo -s
sleep 10m ; /etc/acpi/hibernate.sh
```

---

