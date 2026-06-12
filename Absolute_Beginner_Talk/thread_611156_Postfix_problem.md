---
title: "Postfix problem"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by JonasE on 2007-11-12
Hey, I have edgy and I have installed apahce, mysql, php and now I need to send out emails from a site using php. I installed postfix to the best of my abilities but it doesnt seem to want to work. What happens is I use the php mail() command and I get no errors or anything but I never receive the email. I think my problem is that I dont totally understand what I need for postfix to work. I dont have a domain name of any kind and I dont know if thats the problem or what. If anyone can atleast shed some light on the things that are required for postfix to work that would be awesome.

God bless,
  JonasE.

---

### Post by Daveski on 2007-11-18
You could post your config file (/etc/postfix/main.cf).

postfix is a Mail Transfer Agent which usually sends a message directly to another mail server, or via a smart-host such as your ISP SMTP server. If you are not trying to deliver external emails, and just want the mail delivered to a local user, then you probably need a   local MDA or Mail Delivery Agent.

See [http://ebusiness.gbdirect.co.uk/howtos/mail-system.html](http://ebusiness.gbdirect.co.uk/howtos/mail-system.html)

---

### Post by JonasE on 2007-11-19
Here is my main.cf file - I have a domain name now from 1and1.com and I think im using the right address for being able to use their smtp server to send out external mail, but I obviously am wrong or have another problem.

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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = smtp.1and1.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = smtp.1and1.com, william, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
unknown_local_recipient_reject_code = 450
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

Thanks,
  JonasE

---

### Post by Daveski on 2007-11-19
I think you need to change to:

```
myhostname = host_name_of_your_computer
mydestination = host_name_of_your_computer, localhost.localdomain, localhost
relayhost = smtp.1and1.com
```

---

### Post by JonasE on 2007-11-21
Well, thank you for helping so far, but I still cant seem to get email to work here. I changed the things you had mentioned. I am behind a router and wonder if thats the problem. I have opened ports 25 and 110 on my router to be directed to my server but that doesnt seem to be helping at all. Do you know of any other reasons that might be stopping postfix from working?

---

### Post by JonasE on 2007-11-24
Still cant get it to work, but I just scanned my computer with nmap and found that it shows that I have postfix open on port 25 so I dont think my router is the problem anymore. Just curious, but do I have to tell php that I have postfix or would postfix have done that when it installed?

---

### Post by Daveski on 2007-11-25
> **JonasE said:**
> Still cant get it to work, but I just scanned my computer with nmap and found that it shows that I have postfix open on port 25 so I dont think my router is the problem anymore.

If nmap was run inside your network, then your router is not even part of the equation. The router settings, firewall and port forwarding are only for data that goes through the router - i.e. from internal network to/from external network or vice versa.

I do not know how the PHP mail send routine works, but normally emails are sent (to the local machine) via a connection on port 25. Postfix is listening to this port and will take messages for relaying so long as there are no rules to prevent relaying. You probably do not want port 25 forwarded from the internet to your postfix server as this could allow others to use your server to relay mails - usually for unsavory purposes. Postfix will open an outgoing connection on port 25 to your smart host (your ISP mail server) to relay all outgoing messages - again this will be dealt with via the normal NAT connection handling without having to 'open' or forward port 25 on the router.

I would advise installing webmin which will allow you to change the config of postfix via a web GUI. Here you can also read and compose emails to check that you can indeed send and receive mails with postfix. Finally you need to check HOW the PHP routing sends emails and what components it expects to be running on the machine to facilitate this.

---

### Post by JonasE on 2007-11-27
I have installed webmin and wasn't able to send an email to an external address with it so it doesnt appear to be php that is causing my problems. It has to be  postfix some how. I was able to send an email to another local inbox though so I can tell that postfix is working atleast on my network. Any other suggestions anyone?

---

### Post by Daveski on 2007-11-27
Check the log file which is normally in /var/logs/mail.log

There is a great site for helping checking these logs:
[http://www.onlamp.com/pub/a/onlamp/2004/01/22/postfix.html](http://www.onlamp.com/pub/a/onlamp/2004/01/22/postfix.html)

---

### Post by Mr. C. on 2007-11-29
PHP's mail() command  uses the sendmail compatibility binary, not SMTP.  And postfix's sendmail binary uses postdrop, not SMTP.

What is the output of 

```
mailq
```


Send an email using your method, and then show the /var/log/maillog log entries corresponding to the time you sent the mail.

MrC

---

