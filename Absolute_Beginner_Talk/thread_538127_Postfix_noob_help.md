---
title: "Postfix noob help"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by tmcmulli on 2007-08-29
Ok, I've read everything I can find... and I still can't get my postfix setup to send/receive mail correctly.  I'm sure it has to do something with my hostname/domain, etc.

I'm only forwarding ports 25 and 110 to the Ubuntu box, but I did change my mx record to point from the previous mail server (hosted) to my own IP address, thinking that traffic will get routed to my box via that router.

Also very new to linux in general, so no guarantees that anything is config'd right...

Thanks in advance!

main.cf here:

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = delbuntu
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = $mydomain
mydestination = mail.mcmullin-web.com
mynetworks = 127.0.0.0/8, 192.168.1.0/250
mailbox_size_limit = 0
recipient_delimiter = +
masquerade_domains = mcmullin-web.com
```

---

### Post by tmcmulli on 2007-08-29
Quick update, reinstalled postfix and friends... telnet to localhost works, but not to mail.mydomain.com:

```
tmcmulli@dellbuntu:~$ telnet mail.mcmullin-web.com 25
Trying 205.238.135.154...
Connected to mail.mcmullin-web.com.
Escape character is '^]'.
Connection closed by foreign host.
tmcmulli@dellbuntu:~$ 

```

Any help would be GREATLY appreciated...

---

