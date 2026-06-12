---
title: "What is going on with samba?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-09-04
Place->Network shows many machines. My two windows machines are viewable and navigatable. My two samba machines are pictured, twice, with two different names. Neither of these two are navigatable.

I can do the following...
> 
antsvr@antubuntu:~$ sudo /etc/init.d/samba stop
Password:
 * Stopping Samba daemons...                                             [ OK ] 
antsvr@antubuntu:~$ sudo killall nmbd
antsvr@antubuntu:~$ sudo killall smbd
antsvr@antubuntu:~$ sudo killall winbindd
antsvr@antubuntu:~$ ps -A | grep winbindd
antsvr@antubuntu:~$ ps -A | grep nmbd
antsvr@antubuntu:~$ ps -A | grep smbd
(notice no reply to the ps -A | grep commands.) And I can still access and navigate my two windows shares. I can copy and edit these files. I can't touch my samba shares.

I trimmed my smb.conf to remove any chances of error
> 
antsvr@antubuntu:~$ cat /etc/samba/smb.conf
[global]
workgroup = CYGNEHOME

[homes]
read only = no

[OpenShare]
path = /media/sda7/OpenShare

[SecureShare]
path = /media/sda7/SecureShare


Rebooting makes no difference. What is going on?

---

### Post by stmiller on 2007-09-04
What about users? If you haven't already, you'll have to create a samba user on your box (different from your Ubuntu user).
```

sudo smbpasswd -a *username*

```

---

