---
title: "no longer administrator"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by TEDNUGNT on 2007-05-09
i installed 6.06 on a PC and then upgraded to 6.10 using 'update manager'.

now when i login to my usual username i am no longer considered an 'administrator/root' user so i cannot change some of my network settings.

as far as i know there was only one user account (which used to have administrator privileges) that i initially created during the 6.06 install, besides the default 'root' account obviously.

so can i login as root the usual way at the login screen or do i need to go in through a different route? (i ask that having tried to do so and using my usual password but it doesnt let me)

can i change the restricted user that i am currently logged in as to an 'adminstrator/root' user through the 'terminal'?

what happened? please help.

---

### Post by Kobalt on 2007-05-09
You can configure your accounts from System > Admin. > Users & Groups. 
Something must have been either reseted or deleted during the upgrade process (strange though)...

---

### Post by bapoumba on 2007-05-09
Boot in recovery mode. You'll be root with a # prompt. Run:
```
adduser <your_login_here> admin
reboot
```

Your user will have admin privilege again. Then check:
```
~$ groups
bapoumba adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin

```
and add yourself (**sudo adduser <your_login_here> <whatever_group_here>**) to the default groups if not already in all of these.

edit: not in "bapoumba", that's my login ^^

---

### Post by aysiu on 2007-05-09
More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

