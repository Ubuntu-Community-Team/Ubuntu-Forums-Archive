---
title: "networking"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by ice.man on 2006-04-13
i just followed this [http://easylinux.info/wiki/Ubuntu#How_to_add.2Fedit.2Fdelete_network_users]("http://easylinux.info/wiki/Ubuntu#How_to_add.2Fedit.2Fdelete_network_users")
to enable windows to see my shares on linux but it don't work and i can't see my other linux box




@ubuntu:~$ sudo smbpasswd -a system_username
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user system_username. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_username

---

### Post by echo $USER on 2006-04-13
[QUOTE=ice.man]
@ubuntu:~$ sudo smbpasswd -a system_username
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user system_username. Does this user exist in the UNIX password database ?
Failed to modify password entry for user system_username[/QUOTE]

For the system_username are you using a user name that has already been created and has a /home/user directory?  I think you need to create one or use an existing one.  Then use that user name as system_username.  Hope that helps.  This is why:

Failed to initialise SAM_ACCOUNT for user system_username. Does this user exist in the UNIX password database ?

---

