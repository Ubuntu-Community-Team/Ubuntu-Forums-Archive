---
title: "[SOLVED] gproftpd stays deactivated"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by NoThanksM$ on 2007-08-16
I'm an experienced Windows user but still very new to Linux.  I'm trying to set up an ftp server using gproftpd (wading into the pool as opposed to jumping in) and although I've followed the instructions I've seen here and elsewhere, I can't "activate" the ftp server.  The Status in the upper-right corner of gproftpd stays as "Deactivated" when I click the "Activate" button.  when I start it from the command line, these errors are output:

** (gproftpd:24633): WARNING **: Couldn't find pixmap file: gproftpd.png

(gproftpd:24633): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

But according to another post I saw, these don't keep the program from working.  

Here's my config.  If anyone has any suggestions, they would be greatly appreciated.  I've been battling with this on and off for days now.

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "My FTPD"
ServerAdmin [email]Admin@this.domain.topd[/email]omain
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 64789 64802
MasqueradeAddress gpd.dnsalias.net
TimesGMT off
MaxInstances 3
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayFirstChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 100
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_useradd_upload_path /upload
#gp_html_path /var/www/html/ftp.htm
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
  AllowUser ***********
  DenyALL
</Limit>

<Anonymous /var/ftp/***********>
User **********
Group users
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  CWD XCWD  CDUP XCUP >
 DenyAll
</Limit>
</Anonymous>

---

### Post by NoThanksM$ on 2007-08-17
Bump

Anyone?

---

### Post by NoThanksM$ on 2007-08-22
I was finally able to figure this out myself, so I figured I'd post the solution here for anyone else that has this problem in the future.  

There are several things that might cause gproftpd to stay deactivated, but I had set every option I had seen that might cause this (sorry, I can't remember what all of them were now).  The one thing I didn't know about was that, although I chose "standalone" (as opposed to inetd) for the ServerType, apparently inetd was still running (it was checked in Services under System -> Administration)  Because of this, and because it has a line relating to an ftp server in it, port 21 was already in use, so proftpd couldn't use it for itself.  So I looked in /etc/inetd.conf, found the line relating to ftp, and commented it out.  In my inet.conf file, the line I commented out looked like this:
**ftp	stream	tcp	nowait	root	/usr/sbin/tcpd /usr/sbin/proftpd**
and I commented it out by putting the # sign in front of it.  I was thinking about unchecking inetd in the Services to keep it from starting up altogether, but I had another line uncommented in the file (for VMWare server) so I didn't think that would be a good idea.

Also, if you're interested in how I realized this, I stumbled across something in Secure log (found by going to System -> Administration -> System Log) that said port 21 was already in use.  Doing various Google searches and reading enlightened me to the rest.

One final note - after doing this, I could finally activate gproftpd, but I still couldn't connect to anything other than "localhost" which would obviously only work on my computer.  The solution was to add the line
**DefaultAddress *computers_ip_address***
in the Configuration tab (for "computers_ip_address" it will probably be something like 192.168.x.x if you are have a small home network).  Even though this isn't something that can be changed through one of the other GUI fields, it was necessary for me to be able to connect to the server.

Hope this saves someone a lot of time down the road because I sure wish I had known it before!

---

