---
title: "Postfix mail help"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by smed on 2007-07-18
I have set up a home server on my pc. I've been using a GoDaddy domain to forward to my website. The forwarding works fine and the website loads without any problem. The problem comes when i try to use a simple php form that sends an email to an external address (a comcast.net address). I have php installed on my server and it is fully functional. I believe the problem is with my postfix configuration.

I have followed this tutorial: [https://help.ubuntu.com/7.04/server/C/postfix.html]("https://help.ubuntu.com/7.04/server/C/postfix.html")
and here is the main.cf that i ended up with, exactly as it appears.

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete
# version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = smssonline.info
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.smssonline.info, localhost.localdomain,  localhost, smsson$
relayhost = smtpout.secureserver.net
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reje$
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mynetworks_style = host

inet_protocols = all
mynetworks = 127.0.0.0/32, 192.168.1.100/32

```


When I perform a test using 
```
telnet smssonline.info 25

```
here is what i get.
```
Connected to smssonline.info.
Escape character is '^]'.
220 smssonline.info ESMTP Postfix (Ubuntu)
ehlo smssonline.info
250-smssonline.info
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:test@test.com
250 2.1.0 Ok
rcpt to:smed@comcast.net
554 5.7.1 <smed@comcast.net>: Relay access denied

```

I have a feeling that the parameters i'm using for myhostname and mydestination and others are wrong. If you need to see my Godaddy DNS records, just let me know and i'll PM them to you. If someone could please help me solve this problem, I would greatly appreciate it.

---

### Post by Koybe on 2007-07-18
What do you have in /etc/mailname?

It should be the domain you're sending from : smsonline.info

mydestination = mail.smssonline.info, localhost.localdomain,  localhost, smsson$
That last word with a $ seems strange too. Replace it with your domain name smsonline.info

---

### Post by smed on 2007-07-18
the only line in /etc/mailname is
```
mail.smssonline.info
```

I tried changing it to smssonline.info and restarting postfix, but it didn't work.

I checked the mydestination line that you were referring to, and it looks like it was clipped when i coppied it. Here it is again.

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete
# version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = smssonline.info
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.smssonline.info, localhost.localdomain,  localhost, smssonline.info
relayhost = smtpout.secureserver.net
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
mynetworks_style = host


inet_protocols = all
mynetworks = 127.0.0.0/32, 192.168.1.100/32

```

---

### Post by Koybe on 2007-07-18
I'm no expert with sasl but it seems to me that you tried to put an authentication for using smtp. So when you try to send a mail via telnet it blocks you from sending because you aren't authenticated.

Here is a easier howto : [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)

Could you try backuping your existing main.cf and try with this :
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete
# version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = smssonline.info
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.smssonline.info, localhost.localdomain,  localhost, smssonline.info
relayhost = smtpout.secureserver.net
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks = 127.0.0.0/32, 192.168.1.100/32

```

I don't have a default find around to compare with.

---

### Post by smed on 2007-07-29
I followed the guide you suggested and got everything working, including courier IMAP and POP3. However, I'm still unable to send to an external email address, and my php mail forms are still not working. Here is the error i'm getting.
```

mail from: root@smssonline.info
250 2.1.0 Ok
rcpt to: smed@comcast.net
554 5.7.1 <smed@comcast.net>: Relay access denied

```
I currently have
```
relayhost = smtp.secureserver.net
```
that's the address i found in my Godaddy account, but i'm not sure if it's what i should be using. I've also tried the Comcast smtp.comcast.net, but that didn't work either.

---

