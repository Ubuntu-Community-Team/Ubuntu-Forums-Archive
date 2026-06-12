---
title: "Unable to deliver the mail to internet using Postfix"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by ajzone on 2007-12-07
I am trying to set up Postfix on my laptop which is connected to internet using a router and my ISP is comcast. When I try to send an email to an internet address ( my gmail.com account ) I get the following error

Dec  7 00:09:49 xxxx postfix/pickup[4714]: B174DABE16: uid=0 from=<root>
Dec  7 00:09:49 xxxx postfix/cleanup[4717]: B174DABE16: message-id=<20071207050949.B174DABE16@xxxx.com>
Dec  7 00:09:49 xxxx postfix/qmgr[4698]: B174DABE16: from=<root@xxxx.com>, size=292, nrcpt=1 (queue active)
Dec  7 00:09:49 xxxx postfix/smtp[4719]: certificate verification failed for smtp.comcast.net: num=20:unable to get local issuer certificate
Dec  7 00:09:49 xxxx postfix/smtp[4719]: certificate verification failed for smtp.comcast.net: num=27:certificate not trusted
Dec  7 00:09:50 xxxx postfix/smtp[4719]: B174DABE16: to=<****@gmail.com>, relay=smtp.comcast.net[::ffff:76.96.62.117]:587, delay=0.61, delays=0.2/0.02/0.28/0.1, dsn=5.1.0, status=bounced (host smtp.comcast.net[::ffff:76.96.62.117] said: 550 5.1.0 Authentication required (in reply to MAIL FROM command))

My guess is that my ISP requires to authenticate using some SSL certificate which I dont have on my machine? do i need to get one somehow? or is it some configuration issue? Any help would be really appreciated - AJ

Here is my main.cf file

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# What domain name to use in outbound mails
myorigin = $myhostname

# Domain names to recieve mail for
mydestination = $myhostname localhost.$mydomain localhost $myomain

# Receieve mails from clients on following networks
mynetworks = 127.0.0.0/8, 192.168.0.0/8

# Do not forward mails from strangers
relay_domains = 

# Delivery method on internet
relayhost = [smtp.comcast.net]:587


alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
#fallback_relay = [smtp.comcast.net]:587
#transport_maps = hash:/etc/postfix/postfix-config/transport

---

### Post by kidders on 2007-12-08
> **ajzone said:**
> My guess is that my ISP requires to authenticate using some SSL certificate which I dont have on my machineYou need the right username & password.

Not many SMTP servers are happy to be used as a relay. On the face of it at least, yours seems to be ... but it wants your Postfix to log in first.

---

### Post by llamakc on 2007-12-08
Does /etc/ssl/certs/cacert.pem exist? And have you ran `update-ca-certificates` yet?

---

### Post by kidders on 2007-12-08
> **llamakc said:**
> Does /etc/ssl/certs/cacert.pem exist? And have you ran `update-ca-certificates` yet?Hi there,

The certificate validation messages are a red herring imo ... ajzone's Postfix doesn't *have* to be able to validate what could very well be a self-signed certificate anyway, in order to send mails through a relay.

---

