---
title: "Setting up vsftp server - help!"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by jimbodot on 2005-12-28
Firstly I want to say HELLO! I just installed ubuntu's and it look and feel great!

I am setting up, or trying to, like this

I want my server to have a ftp users list with password
I don't want any anonymous user

Ive been searching this forum for guide but I can't find out how to setup an ftp with a USERS LIST that I can edit

If it's not too much to ask, please show me what to put in my vsftpd.conf, show me what files to edit my user list.

Also I would like to limit the bandwith on demand, from a simple admin remote ftp account.

Thanks!

---

### Post by cstudent on 2005-12-28
Took me awhile to find this thread, but it helped me set up my ftp server. I don't allow annonymous logins and I have two user accounts with read only access. Hopefully it can help you too.

[http://www.ubuntuforums.org/showthread.php?t=91887](http://www.ubuntuforums.org/showthread.php?t=91887)

---

### Post by jimbodot on 2005-12-28
thx, but I already read that

This allow me to put the server up, but how do I add users. Is there a conf file about users or do I need to add user via the local system

---

### Post by cstudent on 2005-12-30
I added a new user to the system and then appended some lines at the end of the vsftpd.conf file for that user account. Below is the active parts of my vsftpd.conf file. I edited out all the disabled sections and and left what is active. I just used the default vsftpd.conf file and made changes to it.

```


# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=NO
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
# You may fully customise the login banner string:
ftpd_banner=Welcome Dudes to Bill's FTP service!!
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
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

# Additional settings made by Bill Kirby
#music_root=/home/music
hide_ids=YES
use_localtime=YES
max_clients=5
max_per_ip=5
hide_file=.*
message_file=.message


```

Hope this helps you.

---

### Post by jimbodot on 2006-01-01
Thanks!

I saw you've put write_enable=NO

That mean they cannot AT ALL write on the ftp, right? If I Enable that, they will be able to write on ftp, right? Now I just need to edit the differents permissions on the folders I've created in their home folder. But does it overwrite those permissions I've edited, or does it simply ALLOW them to write if the permission is set?

---

