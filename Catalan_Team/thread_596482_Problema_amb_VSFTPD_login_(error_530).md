---
title: "Problema amb VSFTPD login (error 530)"
date: 2007-10-29
forum: Catalan Team
---

### Post by txetxubcn on 2007-10-29
He instalar vsftpd y configurat com surt a mil guias pero quan entro em possa error 530 login incorrect... he provat amb varis usuaris y configuracions...
us poso el que tinc actualment a veure si encontreu en que pot fallar perque estic ja..!!!
 ```
/etc/vsftp.conf
```
```

# Run standalone? vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=775
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that turning on ascii_download_enable enables malicious remote parties
# to consume your I/O resources, by issuing the command "SIZE /big/file" in
# ASCII mode.
# These ASCII options are split into upload and download because you may wish
# to enable ASCII uploads (to prevent uploaded scripts etc. from breaking),
# without the DoS risk of SIZE and ASCII downloads. ASCII mangling should be
# on the client anyway..
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to Txetxu FTP.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories. See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default. These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty. Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO
check_shell=NO
```

vaig possar "useradd prueba" amb pass "prueba". el poso dins el grup FTP i creo home/prueba directori.
doncs quan obro el ftp...
```
sergio@sergio-desktop:~$ ftp XXXXX.XX
Connected to XXXXX.XX.
220 FTPU ready.
Name (XXXXX.XX:sergio): prueba
331 Password required for prueba.
Password:
530 Login incorrect.
Login failed.
Remote system type is Ignored.

```
Al vsftpd.chroot_list apareix "prueba"
He vist que a alguns forums posa q es problema del PAM pero he possat /bin/false com shell de login de “prueba” y els problemes no acaban...

mi shell es aquest
```
# /etc/shells: valid login shells
/bin/csh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/sh
/usr/bin/screen
/bin/dash
/bin/bash
/bin/rbash
/bin/false
```

y el meu /etc/pam.d/vsftpd
```
# Standard behaviour for ftpd(8).
auth	required	pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session

@include common-auth
auth	required	pam_shells.so

```

Tambe he probat amb el meu nom de usuari sergio... si activo 
anonymous_enable=YES tampoc puc fer login...

em podeu ajudar??

---

### Post by papapep on 2007-10-29
Has verificat que tens els ports 20 i 21 oberts?

També podries provar a posar-li a l'usuari com a valor de shell /sbin/nologin.

---

### Post by txetxubcn on 2007-10-30
he possat aquest sheel i tampoc...
i en la configuració del router estan oberts el 20 i 22 ports...
si entro per 
ftp localhost
es deixa conectar com anonim pero sino res...

---

### Post by papapep on 2007-10-30
Bé, que puguis entrar com anònim vol dir que només tens problema de configuració dels usuaris autentificats, però que el servidor funciona correctament.
I si proves a posar on has posat /sbin/nologin , **/bin/bash** (atenció, que és /bin, sense la **s**)? Què hi posava abans, /sbin/false, /bin/false?

---

### Post by txetxubcn on 2007-10-30
abans possava bin/bash he provat mil convinacions de shells i res...
lo estrany tambe es que m'entri com 
$ftp localhost
y no com 
$ftp IP_Internet

si entro desde localhost em surt el banner del meu ftp
ftp localhost
Connected to localhost.
220 Weiii! FTP Sergi working NOW!.
Name (localhost:sergio): 


pero si entro desde ftp IP_Internet a sobra de no deixar-me entrar ni com anonim em surt:

$ftp IP_Internet
Connected to IP_Internet.
220 FTPU ready.
Name (IP_Internet:sergio):

---

