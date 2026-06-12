---
title: "[SOLVED] How Can I Remove This???"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by rpainter on 2008-03-13
I installed a copy of Win4Lin on my box, to see if I liked it better than VirtualBox. I have concluded that VirtualBox does everything that I need, and it is free...so I will stick with that.

I have uninstalled Win4Lin, but when I look in my System Monitor, /dev/scd0 is still showing up as /var/win4linpro/mnt. How can I get rid of this?

Screenshot of System Monitor attached.

Thanks.

---

### Post by HermanAB on 2008-03-13
You probably need to do a "umount -l /dev/scd0" and then modify "/etc/fstab".

Cheers,

Herman

---

### Post by rpainter on 2008-03-13
> **HermanAB said:**
> You probably need to do a "umount -l /dev/scd0" and then modify "/etc/fstab".

Cheers,

Herman

Cool. That worked. I tried the umount, but I did not use the -l switch the first time. After I unmounted, I removed the /var/win4linpro directory through the terminal.

Thanks again.

---

