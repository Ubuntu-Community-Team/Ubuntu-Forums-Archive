---
title: "gproftpd configuration"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by treborblack on 2006-09-12
Hi i've got the server running temorarliy for anonymous downloads at 
[ftp://alfaromeo164.dyndns.org](ftp://alfaromeo164.dyndns.org) and can see the upload directory. but i cant upload to it and theres no mention of it in the conf file.
what step have i missed:confused: 

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTPD"
Bind "0.0.0.0"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User nobody
Group nogroup
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /home/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/ftp.html
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser anonymous
  DenyALL
</Limit>

<Anonymous /home/ftp>
User anonymous
Group anonymous
AnonRequirePassword off
MaxClients 2 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
</Anonymous>

Cheers

Treebs

---

