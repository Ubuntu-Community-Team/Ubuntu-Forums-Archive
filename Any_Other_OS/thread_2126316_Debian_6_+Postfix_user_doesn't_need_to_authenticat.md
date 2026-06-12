---
title: "Debian 6 +Postfix user doesn't need to authenticate when sending a mail to himself??"
date: 2013-03-16
forum: Any Other OS
---

### Post by Thavid88 on 2013-03-16
Hi there,

for some time now I have a problem with my postfix configuration and I'm just not able to fix it. I hope, somebody can help me out here, because it's just drives me crazy..

So I have a Debian 6 (64bit)+Postfix +Dovecot server (all packages are up to date). E-mail delivery works great, IMAP and POP3 also and even SSL/TLS with authentication on SMTP relay. I thought that I'm ready, but while I was testing I noticed the following thing: my user (let's call it [email]user@company.com[/email]) can not send e-mails through my server without authentication (which is great, that's exactly what I want), but for some reason he can send an e-mail to himself without auth!!

What I mean is, when I set up a user account in Outlook, if I don't put any auth data for the SMTP relay server, just the correct e-mail address (user@company.com) then I can send an e-mail without a problem to [email]user@company.com[/email]. But I don't want this because that way anybody who knows the e-mail address and the server IP can send e-mails/spams for the user from the user's address..

Does anybody have an idea how to prevent this? I tried a lot of things, including removing the "permit_mynetworks" from smtpd_recipient_restrictions but it didn't work. When I add a simple "reject" at the end of the [COLOR=#333333][FONT=UbuntuBeta][/FONT][/COLOR]smtpd_recipient_restrictions, then it works as expected, but then my user can not recieve e-mails from the outside world..

This realy kills me. Any help will be appreciate.

Here's my main.cf

Thank you very much.

David


[COLOR=#323333][FONT=Tahoma]# See /usr/share/postfix/main.cf.dist for a commented, more complete version[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# should be the FQDN of your machine
myhostname=mail.company.com
# internet domain name of your system.
# Default is to use $myhostname without the sub-domain
mydomain=company.com
# the domain from which local emails will be from: [EMAIL="root@example.org"][COLOR=#DD4814]root@example.org[/COLOR][/EMAIL]
myorigin=$mydomain[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# set to localhost, because we handle all domains via virtual_mailbox_domains
mydestination = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
inet_interfaces = all
mailbox_size_limit = 0
recipient_delimiter = +[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# debug level for messages in log. level 2 is the default one
debug_peer_level=2
# debug request only coming from this IP
#debug_peer_list=127.0.0.1[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# the banner your mail system will greet a client who opens a socket to us
smtpd_banner=$myhostname ESMTP $mail_name
# disable information messages to local users about new emails
biff=no[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# we don't use relayhost, so set it empty
relayhost=[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# disable showing why the user does not exist in your system
show_user_unknown_table_name=no[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# appending .domain is the MUA's job.
append_dot_mydomain = no[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# local aliases for postmaster, root, ...
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# virtual domain options
###############################
# save destination of the incoming mails
virtual_mailbox_base=/var/vmail
# the following 3 files are 2-columns files. I will call the left column the left side handed (LSH) and the right column the right side handed (RSH)
# contains the domain names for which emails will be accepted. The LSH contains the names, the RSH any string but at least one char (e.g. OK)
virtual_mailbox_domains=hash:/etc/postfix/virtual_mailbox_domains
# contains the virtual mailboxes for which emails will be saved on this system. LSH: incoming e-mail address, RSH: location of the mailbox relative to $virt$
virtual_mailbox_maps=hash:/etc/postfix/virtual_mailbox_maps
# contains the redirections. LSH: incoming e-mail address, RSH: forwarding e-mail address, multiple forwading addresses are seperated with comma
virtual_alias_maps=hash:/etc/postfix/virtual_alias_maps[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# userid of the virtual mailbox user we created
virtual_minimum_uid=100
virtual_uid_maps=static:5000
# groupid of the virtual mailbox user we created
virtual_gid_maps=static:5000
# delivery agent we use to save the mails
virtual_transport=dovecot[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]# TLS parameters
###############################
# own certificate
smtpd_tls_cert_file=/etc/apache2/ssl/mail.company.com.pem
smtpd_tls_key_file=/etc/apache2/ssl/mail.company.com.key
# accepted CA certificates
smtpd_tls_CAfile=/etc/ssl/certs/ca-certificates.crt
smtp_tls_CAfile=/etc/ssl/certs/ca-certificates.crt[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]smtp_use_tls=yes
smtpd_use_tls=yes
smtpd_tls_loglevel=1
smtpd_tls_received_header=yes
tls_random_source=dev:/dev/urandom
smtp_tls_note_starttls_offer=yes[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]smtpd_tls_session_cache_timeout=3600s
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]queue_directory=/var/spool/postfix
smtpd_sasl_type=dovecot
smtpd_sasl_path=private/auth
#smtpd_sasl_path=auth/dovecot
smtpd_sasl_auth_enable=yes
broken_sasl_auth_clients=yes[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]smtpd_sasl_security_options=noanonymous
smtpd_sasl_tls_security_options=$smtpd_sasl_security_options
smtpd_sasl_local_domain=$myhostname
smtpd_sasl_application_name=smtpd[/FONT][/COLOR]
[COLOR=#323333][FONT=Tahoma]smtpd_helo_required=yes
smtpd_helo_restrictions=reject_invalid_helo_hostname
smtpd_recipient_restrictions=
permit_mynetworks
permit_sasl_authenticated
reject_unauth_destination
reject_unauth_pipelining
reject_invalid_hostname
reject_non_fqdn_sender
reject_unknown_sender_domain
reject_non_fqdn_recipient
reject_unknown_recipient_domain[/FONT][/COLOR]

---

### Post by Thavid88 on 2013-03-18
Hi,

I found the solution for my own question. It turned out, that what I was missing was the correct order in smtpd_recipient_restrictions. So here it is:

smtpd_recipient_restrictions=
        permit_sasl_authenticated
        reject_non_fqdn_sender,
        reject_non_fqdn_recipient,
        reject_non_fqdn_hostname,
        reject_invalid_hostname,
        permit_mynetworks,
        reject_unauth_pipelining,
        reject_unknown_sender_domain,
        reject_unknown_recipient_domain,
        reject_unauth_destination,
        reject_unknown_client,
        permit

---

