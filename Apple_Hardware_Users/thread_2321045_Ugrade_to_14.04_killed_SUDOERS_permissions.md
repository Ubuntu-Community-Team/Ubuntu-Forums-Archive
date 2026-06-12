---
title: "Ugrade to 14.04 killed SUDOERS permissions"
date: 2016-04-20
forum: Apple Hardware Users
---

### Post by horton3 on 2016-04-20
I am stuck between not having root user read/write access and the inability to see which users have sufficient permissions inside sudoers file.  I am able to ssh to ATV1 but without SUDO root level access to system and files. Each command to proceed with kodi build (post upgrade to UBUNTU 14.04) is met with denied permissions and user (atv) not in sudoers file. F R U S T R A T I N G!!!!!! Please advise

---

### Post by deadflowr on 2016-04-20
post the output for
```
id username
```
(changed username to the user's name you want to see.)

usually not in sudoers file means not in the sudo group in Ubuntu.

---

### Post by horton3 on 2016-04-20
uid=1000(atv) gid=1000(atv) groups=1000(atv),4(adm),6(disk),7(lp),20(dialout),24(cdrom),29(audio),44(video)

---

### Post by deadflowr on 2016-04-20
I see no sudo, which, on Ubuntu, means no sudo/root access.
Always odd, but fixable.

To fix, you can log into a recovery mode, follow this:
[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")
But instead of changing the password, you run this:
```
adduser username sudo
```
then just type *reboot* and let the system reboot to normal Ubuntu.

---

### Post by horton3 on 2016-04-20
the device is an 1st generation apple tv. How do you log into a recovery mode to add the user?

---

### Post by deadflowr on 2016-04-20
> the device is an 1st generation apple tv. How do you log into a recovery mode to add the user?
In that case,
*Thread moved to **Apple Hardware Users**.*

I have no clue about Apple TVs
Hopefully someone else does.

---

### Post by horton3 on 2016-04-20
thank you for trying.

---

### Post by horton3 on 2016-04-20
regardless of command initiated in ssh, the prompt requests [sudo] password for user. When I respond with the user password, it replies that the user is not in the sudoers file. And unfortunately, it will not allow additions to sudoers file. There must be a way to overwrite to gain permissions to access this file and add user to appropriate sudoer group? I am unable to complete kodi install if I am unable to get beyond this point. Surely, there must be a way to break this all down and startover from scratch..

---

