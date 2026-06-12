---
title: "admin privaliges"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by badweasel on 2007-03-09
i know this was probly stupid but i installed ubantu in oem  via alt install and followed instructions and created a new user and deleted the oem profile problem is that i cant do any of the admin stuff (install new progs etc etc) is there any way around this or do i have to do a full reinstall (del partion etc etc) to recover my full privaliges?

---

### Post by igknighted on 2007-03-09
> **badweasel said:**
> i know this was probly stupid but i installed ubantu in oem  via alt install and followed instructions and created a new user and deleted the oem profile problem is that i cant do any of the admin stuff (install new progs etc etc) is there any way around this or do i have to do a full reinstall (del partion etc etc) to recover my full privaliges?

Ewwww, avoid OEM at all costs... Try booting from the live CD (or any live CD) and adding you username to the sudoers file (if you feel comfortable w/ cli try recovery mode for this).

---

### Post by bapoumba on 2007-03-09
Or boot in recovery mode from grub (careful, you will be root) and run ```
adduser <your_login> admin
reboot
```
where <your_login> is your actual user login.

---

