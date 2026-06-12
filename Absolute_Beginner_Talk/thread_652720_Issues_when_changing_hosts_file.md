---
title: "Issues when changing hosts file"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by aruna chandu on 2007-12-29
Hi All,
I am new to ubuntu.
I am facing issues when editing the host file.

I need to change the host file to do some testing.
so i commented local host and pointed to other server.
Next time when i try to edit the host file it says gethostname  not found and thereafter sudo is not working.

can some one help out!!!

Thanks
Aruna Chandu

---

### Post by CatKiller on 2007-12-29
Messing about with the hosts file can indeed muck up your authentication. You can either reboot in recovery (single user) mode, which will automatically log you in as root so that you can restore your backup, or you can boot from the live cd to do the same.

---

### Post by SpacePilot on 2007-12-29
Boot up in safe mode. That will give you a root shell. Change it back, and reboot. You do not want to change localhost settings. localhost is the computer. 

Read up about what /etc/hosts, /etc/hostname, /etc/host.allow, /etc/host.deny does before you start going bananas.

---

