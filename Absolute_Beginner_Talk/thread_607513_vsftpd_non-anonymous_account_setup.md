---
title: "vsftpd non-anonymous account setup?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-11-09
I edited the ftp config file similar to the following for anonymous ftp access.  This setup came from the guide show in the following URL:

[http://ubuntuforums.org/archive/index.php/t-91887.html](http://ubuntuforums.org/archive/index.php/t-91887.html)
```

# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=samurai
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

```

Okay, cool it works but anonymous ftp gives me the creeps and I want to set up a non-anonymous acct. and wanted to know if anyone has a suggested guide or method.  In addtion I would like to use a non-standard ftp port just to make it more difficult on those losers scanning IP's for open port 21.
Any help will be appreciated.

Thanks in advance,

VC

---

### Post by videocheez on 2007-11-11
BUMP:guitar:
I know you youngsters probaly don't use ftp too often but some of you old might be able to help.

---

### Post by carlosjuero on 2007-11-11
For changing the listen port, just add a directive in the .conf file:
```

listen_port=<port #>

```

As for users, I believe vsftp uses the local user list for FTP access (those with permission at least) - take a look at the user_list options on this page: [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html) and see if anything there might help you figure it all out. I haven't configured vsftp for a very long time though, wish I could be more help.

---

### Post by videocheez on 2007-11-12
Thanks for the info. VSFTPD appears to be very versatile.

---

