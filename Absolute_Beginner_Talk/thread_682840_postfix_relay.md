---
title: "postfix relay"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by bradleyd on 2008-01-30
Hello,
does anyone know hot to limit postfix to only send to addresses  in the relay_recipient_maps.
Right know I have my firewall passing smtp traffic to our load balancer. Then the load balancer hands it off to a smtp gateway, which in turn forwards it to the internal mail servers.
Postfix is doing a check on addresses and rejecting ones that are not in the map, but there are some mail getting through that are being sent to @yahoo.com.tw. If I telnet into box and try to send email I get relay denied. If I try relay web testing it comes back negative. I am stumped, I think if I can just limit the rcpt to: to only the addresses in relay_recipient_maps table than all would be good. It sounds like either someone has got a shell or worse inside the network, or postfix is just relaying.
Here is  my main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name GosoloDev
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
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination, reject_non_fqdn_recipient
smtpd_sender_restrictions = reject_unknown_address, reject_unknown_sender_domain
unknown_local_recipient_reject_code = 550
myhostname = gateway1.mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
#myorigin = /etc/mailname
myorigin = $mydomain
mydestination =
local_recipient_maps =
local_transport = error:local mail delivery is disabled
relay_domains = hash:/etc/postfix/relay_domains
relayhost = [192.168.101.193]
relay_recipient_maps = hash:/etc/postfix/gosolo_email
transport_maps = hash:/etc/postfix/trasport_map
mynetworks = 127.0.0.0/8, 192.168.101.0/24
mailbox_size_limit = 0

```
Thanks for your help,
Brad

---

### Post by bradleyd on 2008-01-30
If anyone ever has this problem and wants to know/cares,
I removed permit_mynetworks from smtpd_recipient_restrictions and this has stopped the relay. Our F5(load balancer) passes the smtp traffic to the postfix gateway with an internal address, so postfix see the 192.168.101 address and relays without question. I had 2 possible solutions. 1) figure out how to make F5 seem invisible to the postfix gateway,and pass the the external ip that the mail originated from to postfix. 2) remove permit_mynetworks from restrictions.
If anyone knows a better way, please speak up.
Brad

---

### Post by zazuge on 2008-03-02
I'm new to postfix so I can't reply to your question
but I think Its more useful if you read this
[http://www.postfix.com/STANDARD_CONFIGURATION_README.html#firewall](http://www.postfix.com/STANDARD_CONFIGURATION_README.html#firewall)
hope it'll help ;-)

---

