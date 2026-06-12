---
title: "vsftpd"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Adcuz on 2007-02-13
Hello,

I've been using ubuntu as my server for about 6-8 months, I have just been fiddling with getting vsftpd configured, I have installed it with 

sudo apt-get install vsftpd

OK, it runs fine and I can ftp and it prompts for a password.

BUT I cannot find the vsftpd.conf I have tried searching for it, no luck. Can someone help me?

Oh and I would like to use the in build user account system in ubuntu for usernames and passwords.

---

### Post by DenOK on 2007-02-13
>>> vsftpd.conf

It should be somewhere in /etc, anyway you can always find it

>>> Oh and I would like to use the in build user account system in ubuntu for usernames and passwords.

As far as I remember it is default behaviour, except for root of course.

---

### Post by Adcuz on 2007-02-13
Thankyou so much! that is brilliant. How do I give you beans?

Never mind, I realised it was post count :D

---

### Post by Adcuz on 2007-02-13
What is secure_chroot_dir for and chown_username for?

---

### Post by DenOK on 2007-02-13
Hm, for local user to be able to login make sure that 
local_enable=YES in vsftpd.conf

also you may find explanation of all vsftpd options just google vsftpd.conf and see the examples

---

### Post by Adcuz on 2007-02-13
> **DenOK said:**
> Hm, for local user to be able to login make sure that 
local_enable=YES in vsftpd.conf

also you may find explanation of all vsftpd options just google vsftpd.conf and see the examples

OK, thanks for all your help.

---

### Post by DenOK on 2007-02-13
> **Adcuz said:**
> What is secure_chroot_dir for and chown_username for?


secure_chroot_dir
    This option should be the name of a directory which is empty. Also, the directory should not be writable by the ftp user. This directory is used as a secure chroot() jail at times vsftpd does not require filesystem access.

    Default: /usr/share/empty 

look here

[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

Good Luck!

---

### Post by Adcuz on 2007-02-13
OK, I'm running round in circles now, Everything runs OK, when I try and connect anonymously, it doesnt let me which is what I want. But when I use a local account to log in it times out. and says to check my permissions. What is wrong? (I am using the in built windows client to connect to it)

My config file:

> 

listen=YES
anonymous_enable=no
local_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key




Any ideas?

---

