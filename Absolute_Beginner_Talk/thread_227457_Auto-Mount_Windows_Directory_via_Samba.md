---
title: "Auto-Mount Windows Directory via Samba"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by mumebuhi on 2006-08-01
I am trying to auto-mount a Windows directory via Samba. 

I can only mount the directory manually using smbmount.
$ sudo smbmount //windows_ip/linux$ /media/win -o username="my_username/domain_name"

How can this be done automatically (i.e. every time the machine is rebooted)?

I added the following line to /etc/fstab. But it did not work.
//windows_ip/linux$   /media/win smbfs   credentials=/home/me/.windowscreds,uid=1000,gid=1000 0 0

The .windowscreds file has -rw------- permission and contains:
username=my_username
password=my_password
domain=domain_name

Help?

Thank you.


Buhi

---

### Post by mumebuhi on 2006-08-08
Does anybody have any solutions for this? Thank you.

---

### Post by patrickthebold on 2006-08-08
You could always throw that command in an init script. look in /etc/rc.5

---

### Post by echo $USER on 2006-08-08
> **mumebuhi said:**
> I am trying to auto-mount a Windows directory via Samba. 

I can only mount the directory manually using smbmount.
$ sudo smbmount //windows_ip/linux$ /media/win -o username="my_username/domain_name"

How can this be done automatically (i.e. every time the machine is rebooted)?

I added the following line to /etc/fstab. But it did not work.
//windows_ip/linux$   /media/win smbfs   credentials=/home/me/.windowscreds,uid=1000,gid=1000 0 0

The .windowscreds file has -rw------- permission and contains:
username=my_username
password=my_password
domain=domain_name

Help?

Thank you.


Buhi


Try putting this instead into your fstab...

> //windows_ip/linux$     /media/win      smbfs      default     0   0

---

