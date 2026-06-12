---
title: "Need very good, understandable, reliable help."
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by WorldDrknss on 2006-03-11
I run two websites on windows using apache, mysql, php5, filezilla, and mercury mail, now I have an extra computer around and I Installed ubuntu on to it and installed apache, mysql, php, ftp, and postfix. I have apache mysql and php all up and running, what I need help with is setting up a mail server and ftp server.

For the mail server I need the following.
-Need to be allowed to add individual accounts for users with there own mail boxes
-SMTP Authentication with my isp smtp server.
-Multiple domains

For ftp
-Need to be allowed to add individual account for users and they can only access their folders.

I had read through the postfix configuration in /usr/ folder but did not really understand how to add multiple domains, multiple users accounts, mail boxes and smtp authentication, and I havent check out the ftp config yet.

I run a highly traffic website [http://xampptutorials.com](http://xampptutorials.com) which contains tutorials on how to properly setup and configure xampp for windows.

xampp contains:
This version contains: Apache, MySQL, PHP + PEAR, Perl, mod_php, mod_perl, mod_ssl, OpenSSL, phpMyAdmin, Webalizer, Mercury Mail Transport System for Win32 and NetWare Systems v3.32, JpGraph, FileZilla FTP Server, mcrypt, eAccelerator, SQLite, and WEB-DAV + mod_auth_mysql.

So if anyone could please give me a step by step instructions on how to do what ive listed at the top of this post will be appreciated and it will be added to my site for anyone else who is planning to move to the linux platform, all work will be credited to the person who is able to make a step by step instructions. Must be clear accurate and easy to follow for "anyone" who is making a switch to linux.

Ubuntu 5.10 is the version we will be using if we can get a mail server and ftp server running.

Thanks
[http://xampptutorials.com](http://xampptutorials.com)
-we will be adding a linux section soon, so we are looking for dedicated admins.

---

### Post by WorldDrknss on 2006-03-12
I started looking through postfix and so far I have this

/etc/postfix/main.cf:
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

mydestination = $mydomain $myhostname localhost.$mydomain

virtual_mailbox_domains = xampptutorials.com, clan-revengeance.com, worlddrknss.blogdns.org
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_alias_maps = hash:/etc/postfix/virtual

/etc/postfix/virtual:
[email]WorldDrknss@xampptutorials.com[/email] Administrator
[email]WorldDrknss@clan-revengeance.com[/email] Administrator
[email]Scope@worlddrknss.blogdns.org[/email] Scope

/etc/postfix/vmailbox:
[email]WorldDrknss@xampptutorials.com[/email]    xampptutorials.com
[email]WorldDrknss@clan-revengeance.com[/email]  clan-revengeance.com
[email]Scope@worlddrknss.blogdns.org[/email] scope.worlddrknss.blogdns.org

Im not sure if this is correct being new to linux.
I still need authentication and be able to send mail through my isp smtp server.
thanks

[http://xampptutorials.com](http://xampptutorials.com)

---

