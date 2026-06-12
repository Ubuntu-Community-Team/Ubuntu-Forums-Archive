---
title: "Win 2k Logon Failure"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-04-11
I'm trying to configure my Ubuntu 7.10 server as a samba PDC.

When trying to log a Win 2K machine onto the domain I get this message:
> 
Logon Failed: unknown username or bad password

So there's something wrong with the logon, but how can I check? Is it possible to check all the usernames associated with samba? Also from this Win 2K machine it seems that I can't logon with any usernames or passwords onto the domain.

Any ideas?

---

### Post by superprash2003 on 2008-04-11
have you added a username to samba?

sudo smbpasswd -a system_username

list of sama users in /etc/samba/smbusers

more info on [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by NeonSamurai on 2008-04-14
Hmmm....

I've just checked my /etc/samba/ directory and can't find my smbusers file. Does this mean that I have to create one manually, or should it have been created automatically when I installed and configured samba?

If I do have to create and modify it myself, how do I do that?

If I use a windows account name named Mark and a Linux/Samba account name Mark1 would this be the correct syntax:

> Mark1 = "Mark"

Thanks


Mark

---

### Post by hyper_ch on 2008-04-14
just add a system user to your samba config by the command given above... that's all there is...

---

### Post by NeonSamurai on 2008-04-14
Thanks hyper_ch,

I've tried that but the problem with my Win 2K machine persists. It can see that there's a domain, but it will not recognise the username or password when I try to enter it. Both systems have the same usernames on them now (both Mark) and the passwords are also identical. I've even modified the smbusers file with:
> 
Mark = Mark

I can also log onto my samba server as 'Mark' as well as my Win 2K machine with exactly the same login details.

Any other suggestions (apart from ditching the Win 2K machine)?

Thanks


Mark

---

### Post by hyper_ch on 2008-04-14
check the smb logs why you can't access it...

---

### Post by th00ht on 2008-05-01
> **superprash2003 said:**
> 
sudo smbpasswd -a system_username

Failed to change password for smbuser system_username
(or where systemname=pan and username=j
sudo smbpasswd -a pan_j
Failed to change password for smbuser pan_j

> **superprash2003 said:**
> 
list of sama users in /etc/samba/smbusers

there is no smbusers in /etc/samba

:(

---

### Post by th00ht on 2008-05-01
> **superprash2003 said:**
> 
sudo smbpasswd -a system_username
Failed to change password for smbuser system_username
(or where system name:pan user name:j
sudo smbpasswd -a pan_j
Failed to change password for smbuser pan_j

> **superprash2003 said:**
> 
list of sama users in /etc/samba/smbusers
there is no smbusers in /etc/samba

:(

---

