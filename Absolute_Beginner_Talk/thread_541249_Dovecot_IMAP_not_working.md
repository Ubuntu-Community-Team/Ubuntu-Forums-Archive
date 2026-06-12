---
title: "Dovecot IMAP not working"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by tbone02 on 2007-09-02
I have a 6.06 Lamp server setup with SSH, FTP, postfix, dovecotj, squirrelmail...

I've been able to send mail, ie smtp seems to be working, but the imap server dovecot isn't working.  I've tried to troubleshoot and when I telnet dovecot I get the correct response.

Of course, I'm a noob, and I don't really know what to do at this point.

Should I post some log files or something so that you folks with more experience than me can help?

The dovecot.conf file is very long, so I didn't post it here, but the postfix/main.cf  file is:


```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = mail.mydomain.com, ubuntu, localhost.localdomain, localhost, *.mydomain.com
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain = mydomain.com
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
relay_domains = lists.example.com
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1

masquerade_domains = mydomain.com
masquerade_exceptions = root

maximal_queue_lifetime = 7d

smtp_helo_timeout = 60s
smtpd_recipient_limit = 20
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

```

I would really appreciate any advice because I am stuck.  If there are any other files that would help, please let me know.

Thanks in advance!

---

### Post by tbone02 on 2007-09-02
Here is a snapshot of my most recent /var/log/mail.log:

```
Sep  2 19:27:02 ubuntu postfix/smtp[25964]: warning: host mydomain.com[67.xxx.xx.xxx] greeted me with my own hostname mail.mydomain.com
Sep  2 19:27:02 ubuntu postfix/smtp[25964]: warning: host mydomain.com[67.xxx.xx.xxx] replied to HELO/EHLO with my own hostname mail.mydomain$
Sep  2 19:27:02 ubuntu postfix/smtp[25964]: 80220C9610: to=<patrick@mydomain.com>, orig_to=<patrick>, relay=mydomain.com[67.xxx.xx.xxx], d$
Sep  2 19:27:02 ubuntu postfix/smtpd[25965]: disconnect from unknown[192.168.1.1]
Sep  2 19:27:02 ubuntu postfix/cleanup[25962]: DA5C5C9611: message-id=<20070902232702.DA5C5C9611@mail.mydomain.com>
Sep  2 19:27:02 ubuntu postfix/qmgr[18695]: DA5C5C9611: from=<>, size=4181, nrcpt=1 (queue active)
Sep  2 19:27:02 ubuntu postfix/qmgr[18695]: 80220C9610: removed
Sep  2 19:27:03 ubuntu postfix/smtpd[25965]: connect from unknown[192.168.1.1]
Sep  2 19:27:03 ubuntu postfix/smtp[25964]: warning: host mydomain.com[67.xxx.xx.xxx] greeted me with my own hostname mail.mydomain.com
Sep  2 19:27:03 
Sep  2 19:27:03 ubuntu postfix/smtp[25964]: DA5C5C9611: to=<patrick@mydomain.com>, relay=mydomain.com[67.xxx.xx.xxx], delay=1, status=boun$
Sep  2 19:27:03 ubuntu postfix/qmgr[18695]: DA5C5C9611: removed
Sep  2 19:27:03 ubuntu postfix/smtpd[25965]: disconnect from unknown[192.168.1.1]
Sep  2 19:30:23 ubuntu postfix/anvil[25967]: statistics: max connection rate 2/60s for (smtp:192.168.1.1) at Sep  2 19:27:03
Sep  2 19:30:23 ubuntu postfix/anvil[25967]: statistics: max connection count 1 for (smtp:192.168.1.1) at Sep  2 19:27:02
Sep  2 19:30:23 ubuntu postfix/anvil[25967]: statistics: max cache size 1 at Sep  2 19:27:02
Sep  2 19:34:47 ubuntu postfix/smtpd[25994]: connect from web53802.mail.re2.yahoo.com[206.190.36.197]
Sep  2 19:34:48 ubuntu postfix/smtpd[25994]: NOQUEUE: reject: RCPT from web53802.mail.re2.yahoo.com[206.190.36.197]: 554 <phorne@mydomain.com>: Rel$
Sep  2 19:34:48 ubuntu postfix/smtpd[25994]: disconnect from web53802.mail.re2.yahoo.com[206.190.36.197]
Sep  2 19:35:05 ubuntu dovecot: imap-login: Login: user=<phorne>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
```

As you can see, I sent a test message from my yahoo email account to see what happened.  The message "NOQUEUE: reject: RCPT from ..." seems telling to me.  Unfortunately, I don't know how to fix it.  Scrolling above, there was a message at 19:27:02 that said "(queue active)".

I will continue to research this, but if anyone can give me a heads up as to how to fix this, I'm all ears...

Also, is it a problem that the server keeps issuing this?
```
ubuntu postfix/smtp[25964]: warning: host mydomain.com[67.xxx.xx.xxx] greeted me with my own hostname mail.mydomain.com
```

---

### Post by tbone02 on 2007-09-02
I think I fixed the No queue error by adding these lines to main.cf:

mydomain = mydomain.com

mydestination = mydomain.com

However, I still am not receiving mail.

Here is a snapshot of my log file again:

```
Sep  2 20:08:13 ubuntu postfix/smtpd[26127]: connect from web53809.mail.re2.yahoo.com[206.190.36.204]
Sep  2 20:08:13 ubuntu postfix/smtpd[26127]: A7C77C960B: client=web53809.mail.re2.yahoo.com[206.190.36.204]
Sep  2 20:08:13 ubuntu postfix/cleanup[26132]: A7C77C960B: message-id=<822611.40144.qm@web53809.mail.re2.yahoo.com>
Sep  2 20:08:13 ubuntu postfix/qmgr[26120]: A7C77C960B: from=<username@yahoo.com>, size=1460, nrcpt=1 (queue active)
Sep  2 20:08:13 ubuntu postfix/local[26133]: A7C77C960B: to=<phorne@mydomain.com>, relay=local, delay=0, status=sent (delivered to mailbox)
Sep  2 20:08:13 ubuntu postfix/qmgr[26120]: A7C77C960B: removed
Sep  2 20:08:13 ubuntu postfix/smtpd[26127]: disconnect from web53809.mail.re2.yahoo.com[206.190.36.204]
```

It says the message was delivered to the mailbox, but when I try to check mail with user phorne on squirrelmail, there are no messages.  I also checked in the Maildir directories under /home/phorne/Maildir/ but there were no messages.  To troubleshoot and make sure it wasn't a squirrelmail issue, I tried to check with Outlook and I couldn't logon.  I have no idea if this is related or not.  I used "mail.mydomain.com" for both incoming and outgoing mail in the Outlook configuration.

---

### Post by tbone02 on 2007-09-02
OK...

The mail I send to [email]user@mydomain.com[/email] is being stored at both /var/spool/mail/user and /var/mail/user.

However, I have Maildir mailboxes setup at /home/user/Maildir for each UNIX user.

In the dovecot.conf file I have:

```
default_mail_env = maildir:~/home/%u/Maildir
```

How do I either transfer the messages from /var/spool/mail/user and/or /var/mail/user OR get postfix to deliver the messages to /home/user/Maildir initially?

I'd really appreciate some help.

---

### Post by dougie173 on 2007-09-12
I've been looking at setting up a Dovecote server at home and found this guide:-

[http://adomas.org/2006/08/postfix-dovecot/](http://adomas.org/2006/08/postfix-dovecot/)

In it it mentions that they have:-

default_mail_env = maildir:~/Maildir

As your's (if my memory serves me right) will expand to /home/USER/home/USER/Maildir

---

