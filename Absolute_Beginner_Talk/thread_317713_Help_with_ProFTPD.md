---
title: "Help with ProFTPD"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by wylie31 on 2006-12-12
KDE 3.5
Kubuntu Dapper
PROFTPD (most recent as of Sunday)
GPROFTPD 8.2.2

ftp path to the Apache2 default directory:
var/www/apache2-default/

Hello,

I would appreciate any help that I can get for this problem I am working on. I have been through this site and the Proftpd site looking for answers but no joy.

I am setting up a web development server working in my private LAN. I have everything working fine with the exception of the FTP server. The server runs fine, but will not let me access it from another terminal. When I first installed proftpd I could access with my username wylie50, but had issues with critical errors when uploading files and also could not overwrite old files. As I worked on trying to fix these issues by applying SilverTabs solution to a similar problem ([http://ubuntuforums.org/showthread.php?t=312583&highlight=proftpd](http://ubuntuforums.org/showthread.php?t=312583&highlight=proftpd)) and adjusting the proftpd.conf for overwrite permissions the connections degraded to the point that I now all connections are refused.

A connection through my browser - [ftp://192.168.1.148/](ftp://192.168.1.148/) reads:
The connection to the server was reset while the page was loading.

My FireFTP Message reads:
500 FTP server shut down (Mon Dec 11 17:44:05 2006 , Current connections will be dropped: Mon Dec 11 17:34:05 2006) -- please try again later
Unable to make a connection. Please try again.

When I check on System Services PROFTPD is shown running. I can turn it on and off from the System Settings Page and I can see the changes showing up on GPROFTPD.

My FileZile Message reads:
Status:	Connecting to 192.168.1.148 ...
Status:	Connected with 192.168.1.148. Waiting for welcome message...
Error:	Disconnected from server
Error:	Unable to connect!

It seems that the issue has to be with permissions or authorization of the wylie50 group but I cannot see find any issues. Gproftpd syntax checker has the conf as being good. No routers or firewall issues in this simple LAN network connection.

SilverTab's solution that I applied:
root@wylie31-linux:/var# chmod -R 775 www
root@wylie31-linux:/var# cd /
root@wylie31-linux:/# chgrp -R wylie50 var/www
root@wylie31-linux:/# 

syslog, messages, and all the other logs except the two here do not show any problems.

Logs that might have relevance to the problem:
secure log
Dec 12 10:24:44 wylie31-linux proftpd[12981] localhost
(192.168.1.3[192.168.1.3]): connection refused (Mon Dec 11 17:44:05 2006 ,
Current connections will be dropped: Mon Dec 11 17:34:05 2006) from
192.168.1.3 [192.168.1.3] 

kdm
AUDIT: Tue Dec 12 10:34:53 2006: 4884 X: client 38 rejected from local host
AUDIT: Tue Dec 12 10:34:59 2006: 4884 X: client 38 rejected from local host
AUDIT: Tue Dec 12 10:35:01 2006: 4884 X: client 38 rejected from local host
AUDIT: Tue Dec 12 10:35:01 2006: 4884 X: client 38 rejected from local host


proftpd.conf
```

ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.148"
ServerIdent on "My FTPD"
Bind "192.168.1.148"
ServerAdmin Admin@this.domain.topdomain
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
#User nobody
#Group nobody
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
#gp_useradd_root_path /var/www/apache2-default
#gp_useradd_upload_path /var/www/apache2-default
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
 AllowUser wylie50
 AllowUser wylie31
 DenyALL
</Limit>

<Anonymous /var/www/apache2-default>
User wylie50
Group wylie50
AnonRequirePassword on
MaxClients 30 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite on
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP
XCUP>
AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD
XMKD RMD XRMD>
DenyAll
</Limit>
<Directory /var/www/apache2-default/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE
MKD XMKD  RMD XRMD  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  CDUP XCUP  SITE >
AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY SITE_CHMOD  SITE_CHGRP >
DenyAll
AllowAll
</Limit>
</Directory>
</Anonymous>

<Anonymous /home/ftp>
User wylie31
Group wylie31
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite on
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP
XCUP>
AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD
XMKD RMD XRMD>
DenyAll
</Limit>
<Directory /home/ftp/upload/*>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST MDTM SIZE SITE STAT APPE RETR STOR STOU
MKD XMKD CWD XCWD PWD XPWD CDUP XCUP>
AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY DELE SITE_CHMOD SITE_CHGRP RMD XRMD RNFR RNTO>
DenyAll
</Limit>
</Directory>
</Anonymous> 

```

I am new to this so I am hoping that I just missed something that would be obvious to some of the experts here.

Thank you

---

