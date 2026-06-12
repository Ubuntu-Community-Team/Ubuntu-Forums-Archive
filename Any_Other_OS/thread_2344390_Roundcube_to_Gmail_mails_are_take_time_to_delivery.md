---
title: "Roundcube to Gmail mails are take time to delivery"
date: 2016-11-25
forum: Any Other OS
---

### Post by balas02 on 2016-11-25
hi friend,

   i have installed and configure Roundcube Postfix and dovecot mail server in centos.

  i have problem with my mail server, my local of any user to gmail mails are gotting delivery very slow and take time oneday or four hours to 5 hours, time has changing or differ single mail.

   i have checking through telnet and port is open or not.. all are fine but it take time... 

   please help me 

please see my postfix main.conf file :

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
config_directory = /etc/postfix
daemon_directory = /usr/libexec/postfix
data_directory = /var/lib/postfix
debug_peer_level = 2
default_destination_concurrency_limit = 30
default_process_limit = 30
header_checks = regexp:/etc/postfix/header_checks
header_size_limit = 4096000
home_mailbox = Maildir/
html_directory = no
inet_interfaces = all
inet_protocols = ipv4
mail_owner = postfix
mail_spool_directory = /var/mail local_destination_recipient_limit = 300 local_destination_concurrency_limit = 5
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
mydestination = $myhostname, localhost.$mydomain, localhost,
mydomain = softsolutions4u.info
myhostname = softsolutions4u.info
mynetworks = 192.168.2.0/24, 127.0.0.0/8
mynetworks_style = host
myorigin = $mydomain
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.6.6/README_FILES
recipient_delimiter = +
relay_destination_concurrency_limit = 20
relay_domains = 
relayhost = 
sample_directory = /usr/share/doc/postfix-2.6.6/samples
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtp_tls_note_starttls_offer = yes
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_error_sleep_time = 0
smtpd_helo_required = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination    reject_invalid_hostname,     reject_non_fqdn_sender,     reject_non_fqdn_recipient,     reject_unknown_sender_domain,     reject_unknown_recipient_domain,     reject_unauth_pipelining,         reject_rbl_client bl.spamcop.net     permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = cyrus
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 550
virtual_alias_maps = hash:/etc/postfix/virtual

```
please help me frds...:(:(:(

---

### Post by wildmanne39 on 2016-11-25
*Thread moved to **Any Other OS**.*

---

