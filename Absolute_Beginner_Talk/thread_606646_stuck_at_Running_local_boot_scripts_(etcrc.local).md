---
title: "stuck at Running local boot scripts (/etc/rc.local)"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by sch on 2007-11-08
I'm really new to Linux and this is my first time to use Linux Ubuntu. I've got stuck at the Running local boot scripts (/etc/rc.local) and I've done some research on the previous treads but still can't solve it. 

So I forced my desktop (Dell Optiplex GX270) to shut down and reboot it but this time I chose to boot in recovery mode and it stuck again when came to:

$Mounting securityfs on /sys/kernel/security: done.
Loading AppArmor profiles : done.
* Checking minimum space in /tmp...  [OK]
* Configuring network interfaces...  [OK]
* Setting up console font and keymap... [OK]
root@test:~# * Reloading /etc/samba/smb.conf...

what should I do next? :confused:

---

### Post by Afkpuz on 2007-11-08
Are you dual-booting?

---

### Post by cubeist on 2007-11-08
It looks like it is stopping when it is trying to load a samba configuration file.  Have you done anything to set up a samba network?

To fix it, boot from the live cd... navigate to that trouble file /etc/samba/smb.conf and see if there is anything plainly wrong with the file... or just back up the file and then delete it and reboot... if it still hangs at least you know it wasn't the smb.conf file and we can troubleshoot further...

---

### Post by sch on 2007-11-09
for Afkpuz, yes as I'm having Win XP on the same machine as well.

and for cubeist, I didn't do anything special when setting up the Samba. I remember it used to ask me for Hostname, Account name and Password, MYSQL password and that's all. After that, I just let it run the setup process itself.

sorry to ask but how and where can I find the smb.conf file and delete it?

---

### Post by cubeist on 2007-11-09
well the samba conf file is exactly where the error message says it is... /etc/samba/smb.conf

once you find it, you could delete it, or better yet, just rename it.

---

