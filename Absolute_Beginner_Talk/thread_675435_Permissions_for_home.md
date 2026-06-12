---
title: "Permissions for /home"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Frogbarf on 2008-01-22
For purposes of discussion, take "george" as the admin user and "harry" represent the various ordinary users.

With default permissions on /home, the harrys can see every username on the system, including "george". Since one of the security features of Ubuntu is using a privileged, non-root user to perform system maintenance, so intruders have to figure out not just a password but a username as well, I consider revealing "george" to the ordinary users Not A Good Thing.

I would like to set the permissions on /home so the harrys can't see the subdirectories under it, but george can.

george belongs to the groups "george" and "users".

/home is owned by root. Permissions are for user root, group root, and everyone else.

I added george to the root group and set permissions to 771 (rwxrwx--x), but george still can't list the contents of /home. Is that because george's default group isn't root?

I tried changing george's main group to root, but that doesn't help.

In one word, HELP! Am I trying to do the impossible, or am I just confused?:confused:

---

### Post by p_quarles on 2008-01-22
A little of both. ;)

If you don't want normal users to see any part of the home directory except their own sub-dir, you will also need to make it inaccessible to "george." "george" is, after all, a normal user -- but a normal user that also has access to root privileges using "sudo" and "gksudo." 

There's no reason to add "george" to the root group, btw. That more or less defeats the purpose of having a separate admin account.

---

### Post by bodhi.zazen on 2008-01-22
```
chmod 770 $HOME
```

The system files are different as one needs to have ro acces to most of them, best not to mess with system files.

---

