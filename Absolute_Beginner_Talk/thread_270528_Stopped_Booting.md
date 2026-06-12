---
title: "Stopped Booting"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Chaosopher on 2006-10-03
I installed ubuntu on a partition.  It was working fine for a couple of weeks, but now the option screen doesnt come up, and I go straight into windows.

---

### Post by wpshooter on 2006-10-03
Have you had any problems with machine shutting down prematurely ?  Either by problems with hardware and/or power interruptions caused by storms, or utility power line work.

Have you checked the integrity of your hard drive by running the manufacturers diagnostic software on it.  Sounds like to me you may have either problems with your hard drive or your power supply.

---

### Post by D10 on 2006-10-03
Have you had any problems with Windows? Did you restore, reinstall, or make changes to Windows?

Sounds like to me your MBR has been overwritten. See if this helps
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Chaosopher on 2006-10-03
I dont believe that it has been shut down prematurely, but I am not the only user on the computer.  Thank you for your help.

---

### Post by wpshooter on 2006-10-03
> **Chaosopher said:**
> I dont believe that it has been shut down prematurely, but I am not the only user on the computer.  Thank you for your help.

Then my **guess** is that that is probably the source of your problems.  

Did the other user(s) know that you had installed Ubuntu ?  

Were they aware of how to use it, etc. ?

Have you ask them if they have made any alterations to the computer, particularly to the GRUB that you cause it to not be displayed ?

---

### Post by bigken on 2006-10-03
sounds like someone has run fixmbr and overwriten the grub menu :-k

---

