---
title: "vsftpd using ssl stops umask working"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by mattdrinks on 2007-06-22
I have installed Ubuntu 7.04 Server with the LAMP option.

I have installed and setup vsftpd to use as my ftp server.
But when ever I upload a file using SSL the files always end up with permissions of 
```

- rw- r-- r-- 

```

This is my vsftpdconf file:
```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=0002
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/certfileshere/vsftpd.pem
rsa_private_key_file=/etc/certfileshere/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

```

If I turn off SSL and upload a file then I get the permissions I am after which are:
```

- rw- rw- r-- 

```
How can I get these permissions for files uploaded using SSL.

Thank you for any help.
Matt

---

### Post by alan_daniel on 2007-06-22
I personally am not comfortable enough with SSL to know the answer to this question, but I do know that it's not too terribly inconvenient to just change the permissions manually every now and then. I assume you have one directory that those uploads always go to? You could every now and then just run this in a terminal:

```
sudo chmod -R 664 /(directory)
```

You could even set up just a simple little shell script and put it on a schedule to run every day or something like that, to ensure that it is done every day.

Again, I know this isn't an answer to your question, but I hope it helps.

---

### Post by mattdrinks on 2007-06-24
Thank you,

I am currently using the manual method you mention above, but I was hoping that there was a setting in vsftpd that would enable it to work automatically.

I am going to have a look at setting a script (my first ever) to run on a regular basis as you suggest, would it be sensible to have this script run every 5-10 minutes or would this overburden the server?

I will keep on searching for the ideally solution of having it work automatically on new files uploaded by vsftpd and if I find an answer will post back here.

---

