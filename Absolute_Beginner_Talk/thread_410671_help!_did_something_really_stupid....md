---
title: "help! did something really stupid..."
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by helane on 2007-04-16
don't ask why.. please.. :)

i turned off the administration privileges for the default account (not the root) that was created after installing 7.04 which i was using by default... i did it in the graphic window - not the console, i am not very good with it yet.

now cannot use the system/prefernces options at all...
how to get it back???

thank you guys.

helane.

---

### Post by bwhite82 on 2007-04-16
Ok, firstly, set an SU password:
> 
sudo su -c passwd

Then login to root:
> 
su

Then type:

> gnome-control-center

Then click on users and groups and fix your old account.

---

### Post by helane on 2007-04-16
ok it worked...

now, could you please explain what the commands were? i like to know what i am doing and don't exactly understand...

ty again! h.

---

### Post by Famicommie on 2007-04-16
You turned on the normally disabled root account, logged into it, and fixed your group settings.

---

### Post by dfreer on 2007-04-16
Yeah, basically ubuntu sets up two accounts. Your normal user with limited privileges, and the all powerful root account which can do everything. It ships with absolutely NO password set for the root account, effectively preventing anyone from logging in as root directly.
The first command sudo su -c passwd created a password for the root account, so that you could login as root with the second command. The third command just launched the users GUI so that you could fix it.

A good tip would be to disable that root account's password now that you've fixed your system. Make sure you do that ;)

---

### Post by bwhite82 on 2007-04-16
> **dfreer said:**
> A good tip would be to disable that root account's password now that you've fixed your system. Make sure you do that ;)

Ah yes, good point, the following command will accomplish that:

> sudo passwd -l root

---

### Post by helane on 2007-05-13
thank you... fixed everything :)

---

