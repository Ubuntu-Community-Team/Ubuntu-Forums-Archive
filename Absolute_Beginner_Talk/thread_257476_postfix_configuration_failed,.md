---
title: "postfix configuration failed,"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-09-14
I realised I had actually asked two questions in one post and titled for the other so I thought i'd ask this seperately.

I have recently got Postfix Configuration Failed when I see what is booting up and have lost sound (I think as a consequence) how can I fix this error?

Calv

---

### Post by ape on 2006-09-14
You really need to post the output of the error that postfix is having.  Try executing 'sudo /etc/init.d/postfix restart' and see if any errors are shown.

---

### Post by calvinthomas on 2006-09-14
Doesn't give any error just goes to a prompt like this:

>

---

### Post by ape on 2006-09-15
What about the /var/log/mail.log, mail.info or mail.err files?

---

### Post by Anduu on 2006-09-15
Postfix has nothing to do with the sound system...It is the Linux mail system

I think there was an issue with the latest kernel update affecting sound, video and networking for some people...
Look here to see if you are one of these folks...

[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by calvinthomas on 2006-09-15
> **ape said:**
> What about the /var/log/mail.log, mail.info or mail.err files?
[B]
/var/log/mail.log[/B]

Sep 12 21:33:09 localhost postfix/master[12921]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 12 21:39:00 localhost postfix/master[5161]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 12 21:54:04 localhost postfix/master[5161]: terminating on signal 15
Sep 12 21:55:34 localhost postfix/master[5278]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 12 21:59:14 localhost postfix/master[5302]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 09:31:43 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 09:52:47 localhost postfix/master[5300]: terminating on signal 15
Sep 13 09:54:10 localhost postfix/master[5295]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 10:46:23 localhost postfix/master[5295]: terminating on signal 15
Sep 13 10:47:56 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 12:11:53 localhost postfix/master[5322]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 13:57:48 localhost postfix/master[5322]: terminating on signal 15
Sep 13 14:54:04 localhost postfix/master[5299]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 15:32:11 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 13 17:09:33 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 13 18:30:59 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 13 22:38:31 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 14 00:17:23 localhost postfix/master[5299]: terminating on signal 15
Sep 14 00:18:48 localhost postfix/master[5307]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 00:28:55 localhost postfix/master[5307]: terminating on signal 15
Sep 14 10:20:05 localhost postfix/master[5298]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 12:56:12 localhost postfix/master[5298]: terminating on signal 15
Sep 14 12:57:44 localhost postfix/master[5305]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 13:43:27 localhost postfix/master[5305]: terminating on signal 15
Sep 14 13:56:27 localhost postfix/master[5284]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 14:10:46 localhost postfix/master[5284]: terminating on signal 15
Sep 14 14:12:11 localhost postfix/master[5295]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 14:30:36 localhost postfix/master[5295]: terminating on signal 15
Sep 14 14:32:01 localhost postfix/master[5297]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 14:52:01 localhost postfix/master[5297]: terminating on signal 15
Sep 14 18:05:48 localhost postfix/master[5292]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:20:50 localhost postfix/master[5292]: terminating on signal 15
Sep 14 19:22:15 localhost postfix/master[5310]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:28:26 localhost postfix/master[5310]: terminating on signal 15
Sep 14 19:29:47 localhost postfix/master[5319]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:43:43 localhost postfix/master[5319]: terminating on signal 15
Sep 14 19:45:09 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:56:18 localhost postfix/master[5300]: terminating on signal 15
Sep 14 19:57:42 localhost postfix/master[5318]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 20:16:04 localhost postfix/master[5318]: terminating on signal 15
Sep 14 20:17:29 localhost postfix/master[5325]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 21:07:30 localhost postfix/master[5325]: terminating on signal 15
Sep 14 21:09:01 localhost postfix/master[5305]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 21:36:49 localhost postfix/master[5305]: terminating on signal 15
Sep 14 21:38:18 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 21:57:52 localhost postfix/master[5300]: terminating on signal 15
Sep 14 21:59:16 localhost postfix/master[5324]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 22:29:47 localhost postfix/master[5317]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 22:33:45 localhost postfix/master[5317]: terminating on signal 15
Sep 14 22:35:17 localhost postfix/master[5303]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 23:51:21 localhost postfix/master[5303]: terminating on signal 15
Sep 14 23:52:47 localhost postfix/master[5323]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 23:54:13 localhost postfix/master[5323]: terminating on signal 15
Sep 15 09:22:36 localhost postfix/master[5321]: daemon started -- version 2.2.10, configuration /etc/postfix

**/var/log/mail.info**

Sep 12 21:33:09 localhost postfix/master[12921]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 12 21:39:00 localhost postfix/master[5161]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 12 21:54:04 localhost postfix/master[5161]: terminating on signal 15
Sep 12 21:55:34 localhost postfix/master[5278]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 12 21:59:14 localhost postfix/master[5302]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 09:31:43 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 09:52:47 localhost postfix/master[5300]: terminating on signal 15
Sep 13 09:54:10 localhost postfix/master[5295]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 10:46:23 localhost postfix/master[5295]: terminating on signal 15
Sep 13 10:47:56 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 12:11:53 localhost postfix/master[5322]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 13:57:48 localhost postfix/master[5322]: terminating on signal 15
Sep 13 14:54:04 localhost postfix/master[5299]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 13 15:32:11 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 13 17:09:33 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 13 18:30:59 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 13 22:38:31 localhost postfix/master[5299]: reload configuration /etc/postfix
Sep 14 00:17:23 localhost postfix/master[5299]: terminating on signal 15
Sep 14 00:18:48 localhost postfix/master[5307]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 00:28:55 localhost postfix/master[5307]: terminating on signal 15
Sep 14 10:20:05 localhost postfix/master[5298]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 12:56:12 localhost postfix/master[5298]: terminating on signal 15
Sep 14 12:57:44 localhost postfix/master[5305]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 13:43:27 localhost postfix/master[5305]: terminating on signal 15
Sep 14 13:56:27 localhost postfix/master[5284]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 14:10:46 localhost postfix/master[5284]: terminating on signal 15
Sep 14 14:12:11 localhost postfix/master[5295]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 14:30:36 localhost postfix/master[5295]: terminating on signal 15
Sep 14 14:32:01 localhost postfix/master[5297]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 14:52:01 localhost postfix/master[5297]: terminating on signal 15
Sep 14 18:05:48 localhost postfix/master[5292]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:20:50 localhost postfix/master[5292]: terminating on signal 15
Sep 14 19:22:15 localhost postfix/master[5310]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:28:26 localhost postfix/master[5310]: terminating on signal 15
Sep 14 19:29:47 localhost postfix/master[5319]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:43:43 localhost postfix/master[5319]: terminating on signal 15
Sep 14 19:45:09 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 19:56:18 localhost postfix/master[5300]: terminating on signal 15
Sep 14 19:57:42 localhost postfix/master[5318]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 20:16:04 localhost postfix/master[5318]: terminating on signal 15
Sep 14 20:17:29 localhost postfix/master[5325]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 21:07:30 localhost postfix/master[5325]: terminating on signal 15
Sep 14 21:09:01 localhost postfix/master[5305]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 21:36:49 localhost postfix/master[5305]: terminating on signal 15
Sep 14 21:38:18 localhost postfix/master[5300]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 21:57:52 localhost postfix/master[5300]: terminating on signal 15
Sep 14 21:59:16 localhost postfix/master[5324]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 22:29:47 localhost postfix/master[5317]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 22:33:45 localhost postfix/master[5317]: terminating on signal 15
Sep 14 22:35:17 localhost postfix/master[5303]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 23:51:21 localhost postfix/master[5303]: terminating on signal 15
Sep 14 23:52:47 localhost postfix/master[5323]: daemon started -- version 2.2.10, configuration /etc/postfix
Sep 14 23:54:13 localhost postfix/master[5323]: terminating on signal 15
Sep 15 09:22:36 localhost postfix/master[5321]: daemon started -- version 2.2.10, configuration /etc/postfix
[B]
/var/log/mail.err[/B] is empty

Thankyou for your continued help

Calv

---

### Post by ape on 2006-09-15
Okay, so postfix is dying right away with a signal 15.  What information do you get if you try the following command:

 ```
sudo /usr/sbin/postfix -vvv
```

might be printed to the screen or it might be in the mail.log file.

---

### Post by calvinthomas on 2006-09-15
I'm not sure if this is all of the output but its all that I can get from the terminal:

postfix: vstream_buf_get_ready: fd 4 got 1191
postfix: dict_update: smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
postfix: dict_update: biff = no
postfix: dict_update: append_dot_mydomain = no
postfix: dict_update: smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: dict_update: smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
postfix: dict_update: smtpd_use_tls = yes
postfix: dict_update: smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
postfix: dict_update: smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
postfix: dict_update: myhostname = localhost
postfix: dict_update: alias_maps = hash:/etc/aliases
postfix: dict_update: alias_database = hash:/etc/aliases
postfix: dict_update: mydestination = localhost, localhost.localdomain, , localhost
postfix: dict_update: relayhost = 
postfix: dict_update: mynetworks = 127.0.0.0/8
postfix: dict_update: mailbox_command = procmail -a "$EXTENSION"
postfix: dict_update: mailbox_size_limit = 0
postfix: dict_update: recipient_delimiter = +
postfix: dict_update: inet_interfaces = all
postfix: vstream_buf_get_ready: fd 4 got 318
postfix: dict_lookup: syslog_facility = (notfound)
postfix: mac_parse: mail
postfix: dict_eval: const  mail
postfix: dict_update: syslog_facility = mail
postfix: dict_lookup: inet_protocols = (notfound)
postfix: mac_parse: ipv4
postfix: dict_eval: const  ipv4
postfix: dict_update: inet_protocols = ipv4
postfix: name_mask: ipv4
postfix: dict_lookup: myhostname = localhost
postfix: mac_parse: localhost
postfix: dict_eval: const  localhost
postfix: dict_lookup: mydomain = (notfound)
postfix: mac_parse: localhost
postfix: dict_eval: const  localhost
postfix: dict_update: mydomain = localhost
postfix: dict_lookup: mail_name = (notfound)
postfix: mac_parse: Postfix
postfix: dict_eval: const  Postfix
postfix: dict_update: mail_name = Postfix
postfix: dict_lookup: syslog_name = (notfound)
postfix: mac_parse: postfix
postfix: dict_eval: const  postfix
postfix: dict_update: syslog_name = postfix
postfix: dict_lookup: mail_owner = (notfound)
postfix: mac_parse: postfix
postfix: dict_eval: const  postfix
postfix: dict_update: mail_owner = postfix
postfix: dict_lookup: setgid_group = (notfound)
postfix: mac_parse: postdrop
postfix: dict_eval: const  postdrop
postfix: dict_update: setgid_group = postdrop
postfix: dict_lookup: mydestination = localhost, localhost.localdomain, , localhost
postfix: mac_parse: localhost, localhost.localdomain, , localhost
postfix: dict_eval: const  localhost, localhost.localdomain, , localhost
postfix: dict_lookup: myorigin = (notfound)
postfix: mac_parse: $myhostname
postfix: dict_lookup: myhostname = localhost
postfix: mac_parse: localhost
postfix: dict_eval: expand $myhostname -> localhost
postfix: dict_update: myorigin = localhost
postfix: dict_lookup: relayhost = 
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_lookup: daemon_directory = (notfound)
postfix: mac_parse: /usr/lib/postfix
postfix: dict_eval: const  /usr/lib/postfix
postfix: dict_update: daemon_directory = /usr/lib/postfix
postfix: dict_lookup: command_directory = (notfound)
postfix: mac_parse: /usr/sbin
postfix: dict_eval: const  /usr/sbin
postfix: dict_update: command_directory = /usr/sbin
postfix: dict_lookup: queue_directory = (notfound)
postfix: mac_parse: /var/spool/postfix
postfix: dict_eval: const  /var/spool/postfix
postfix: dict_update: queue_directory = /var/spool/postfix
postfix: dict_lookup: process_id_directory = (notfound)
postfix: mac_parse: pid
postfix: dict_eval: const  pid
postfix: dict_update: process_id_directory = pid
postfix: dict_lookup: inet_interfaces = all
postfix: mac_parse: all
postfix: dict_eval: const  all
postfix: dict_lookup: proxy_interfaces = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: proxy_interfaces = 
postfix: dict_lookup: double_bounce_sender = (notfound)
postfix: mac_parse: double-bounce
postfix: dict_eval: const  double-bounce
postfix: dict_update: double_bounce_sender = double-bounce
postfix: dict_lookup: default_privs = (notfound)
postfix: mac_parse: nobody
postfix: dict_eval: const  nobody
postfix: dict_update: default_privs = nobody
postfix: dict_lookup: alias_database = hash:/etc/aliases
postfix: mac_parse: hash:/etc/aliases
postfix: dict_eval: const  hash:/etc/aliases
postfix: dict_lookup: mail_release_date = (notfound)
postfix: mac_parse: 20060405
postfix: dict_eval: const  20060405
postfix: dict_update: mail_release_date = 20060405
postfix: dict_lookup: mail_version = (notfound)
postfix: mac_parse: 2.2.10
postfix: dict_eval: const  2.2.10
postfix: dict_update: mail_version = 2.2.10
postfix: dict_lookup: default_database_type = (notfound)
postfix: mac_parse: hash
postfix: dict_eval: const  hash
postfix: dict_update: default_database_type = hash
postfix: dict_lookup: hash_queue_names = (notfound)
postfix: mac_parse: deferred, defer
postfix: dict_eval: const  deferred, defer
postfix: dict_update: hash_queue_names = deferred, defer
postfix: dict_lookup: recipient_delimiter = +
postfix: mac_parse: +
postfix: dict_eval: const  +
postfix: dict_lookup: relay_domains = (notfound)
postfix: mac_parse: $mydestination
postfix: dict_lookup: mydestination = localhost, localhost.localdomain, , localhost
postfix: mac_parse: localhost, localhost.localdomain, , localhost
postfix: dict_eval: expand $mydestination -> localhost, localhost.localdomain, , localhost
postfix: dict_update: relay_domains = localhost, localhost.localdomain, , localhost
postfix: dict_lookup: fast_flush_domains = (notfound)
postfix: mac_parse: $relay_domains
postfix: dict_lookup: relay_domains = localhost, localhost.localdomain, , localhost
postfix: mac_parse: localhost, localhost.localdomain, , localhost
postfix: dict_eval: expand $relay_domains -> localhost, localhost.localdomain, , localhost
postfix: dict_update: fast_flush_domains = localhost, localhost.localdomain, , localhost
postfix: dict_lookup: export_environment = (notfound)
postfix: mac_parse: TZ MAIL_CONFIG
postfix: dict_eval: const  TZ MAIL_CONFIG
postfix: dict_update: export_environment = TZ MAIL_CONFIG
postfix: dict_lookup: import_environment = (notfound)
postfix: mac_parse: MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
postfix: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
postfix: dict_update: import_environment = MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
postfix: dict_lookup: mynetworks_style = (notfound)
postfix: mac_parse: subnet
postfix: dict_eval: const  subnet
postfix: dict_update: mynetworks_style = subnet
postfix: dict_lookup: debug_peer_list = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: debug_peer_list = 
postfix: dict_lookup: default_verp_delimiters = (notfound)
postfix: mac_parse: +=
postfix: dict_eval: const  +=
postfix: dict_update: default_verp_delimiters = +=
postfix: dict_lookup: verp_delimiter_filter = (notfound)
postfix: mac_parse: -=+
postfix: dict_eval: const  -=+
postfix: dict_update: verp_delimiter_filter = -=+
postfix: dict_lookup: parent_domain_matches_subdomains = (notfound)
postfix: mac_parse: debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
postfix: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
postfix: dict_update: parent_domain_matches_subdomains = debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
postfix: dict_lookup: alternate_config_directories = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: alternate_config_directories = 
postfix: dict_lookup: bounce_service_name = (notfound)
postfix: mac_parse: bounce
postfix: dict_eval: const  bounce
postfix: dict_update: bounce_service_name = bounce
postfix: dict_lookup: cleanup_service_name = (notfound)
postfix: mac_parse: cleanup
postfix: dict_eval: const  cleanup
postfix: dict_update: cleanup_service_name = cleanup
postfix: dict_lookup: defer_service_name = (notfound)
postfix: mac_parse: defer
postfix: dict_eval: const  defer
postfix: dict_update: defer_service_name = defer
postfix: dict_lookup: pickup_service_name = (notfound)
postfix: mac_parse: pickup
postfix: dict_eval: const  pickup
postfix: dict_update: pickup_service_name = pickup
postfix: dict_lookup: queue_service_name = (notfound)
postfix: mac_parse: qmgr
postfix: dict_eval: const  qmgr
postfix: dict_update: queue_service_name = qmgr
postfix: dict_lookup: rewrite_service_name = (notfound)
postfix: mac_parse: rewrite
postfix: dict_eval: const  rewrite
postfix: dict_update: rewrite_service_name = rewrite
postfix: dict_lookup: showq_service_name = (notfound)
postfix: mac_parse: showq
postfix: dict_eval: const  showq
postfix: dict_update: showq_service_name = showq
postfix: dict_lookup: error_service_name = (notfound)
postfix: mac_parse: error
postfix: dict_eval: const  error
postfix: dict_update: error_service_name = error
postfix: dict_lookup: flush_service_name = (notfound)
postfix: mac_parse: flush
postfix: dict_eval: const  flush
postfix: dict_update: flush_service_name = flush
postfix: dict_lookup: address_verify_service_name = (notfound)
postfix: mac_parse: verify
postfix: dict_eval: const  verify
postfix: dict_update: address_verify_service_name = verify
postfix: dict_lookup: trace_service_name = (notfound)
postfix: mac_parse: trace
postfix: dict_eval: const  trace
postfix: dict_update: trace_service_name = trace
postfix: dict_lookup: tls_random_exchange_name = (notfound)
postfix: mac_parse: ${config_directory}/prng_exch
postfix: dict_lookup: config_directory = /etc/postfix
postfix: mac_parse: /etc/postfix
postfix: dict_eval: expand ${config_directory}/prng_exch -> /etc/postfix/prng_exch
postfix: dict_update: tls_random_exchange_name = /etc/postfix/prng_exch
postfix: dict_lookup: smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: mac_parse: /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: dict_eval: const  /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: dict_lookup: smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
postfix: mac_parse: /etc/ssl/private/ssl-cert-snakeoil.key
postfix: dict_eval: const  /etc/ssl/private/ssl-cert-snakeoil.key
postfix: dict_lookup: smtpd_tls_dcert_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_dcert_file = 
postfix: dict_lookup: smtpd_tls_dkey_file = (notfound)
postfix: mac_parse: $smtpd_tls_dcert_file
postfix: dict_lookup: smtpd_tls_dcert_file = 
postfix: dict_eval: expand $smtpd_tls_dcert_file -> 
postfix: dict_update: smtpd_tls_dkey_file = 
postfix: dict_lookup: smtpd_tls_CAfile = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_CAfile = 
postfix: dict_lookup: smtpd_tls_CApath = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_CApath = 
postfix: dict_lookup: smtpd_tls_cipherlist = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_cipherlist = 
postfix: dict_lookup: smtpd_tls_dh512_param_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_dh512_param_file = 
postfix: dict_lookup: smtpd_tls_dh1024_param_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_dh1024_param_file = 
postfix: dict_lookup: smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
postfix: mac_parse: btree:${queue_directory}/smtpd_scache
postfix: dict_lookup: queue_directory = /var/spool/postfix
postfix: mac_parse: /var/spool/postfix
postfix: dict_eval: expand btree:${queue_directory}/smtpd_scache -> btree:/var/spool/postfix/smtpd_scache
postfix: dict_lookup: smtp_tls_cert_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_cert_file = 
postfix: dict_lookup: smtp_tls_key_file = (notfound)
postfix: mac_parse: $smtp_tls_cert_file
postfix: dict_lookup: smtp_tls_cert_file = 
postfix: dict_eval: expand $smtp_tls_cert_file -> 
postfix: dict_update: smtp_tls_key_file = 
postfix: dict_lookup: smtp_tls_dcert_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_dcert_file = 
postfix: dict_lookup: smtp_tls_dkey_file = (notfound)
postfix: mac_parse: $smtp_tls_dcert_file
postfix: dict_lookup: smtp_tls_dcert_file = 
postfix: dict_eval: expand $smtp_tls_dcert_file -> 
postfix: dict_update: smtp_tls_dkey_file = 
postfix: dict_lookup: smtp_tls_CAfile = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_CAfile = 
postfix: dict_lookup: smtp_tls_CApath = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_CApath = 
postfix: dict_lookup: smtp_tls_cipherlist = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_cipherlist = 
postfix: dict_lookup: smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
postfix: mac_parse: btree:${queue_directory}/smtp_scache
postfix: dict_lookup: queue_directory = /var/spool/postfix
postfix: mac_parse: /var/spool/postfix
postfix: dict_eval: expand btree:${queue_directory}/smtp_scache -> btree:/var/spool/postfix/smtp_scache
postfix: dict_lookup: max_use = (notfound)
postfix: dict_update: max_use = 100
postfix: dict_lookup: dont_remove = (notfound)
postfix: dict_update: dont_remove = 0
postfix: dict_lookup: line_length_limit = (notfound)
postfix: dict_update: line_length_limit = 2048
postfix: dict_lookup: message_size_limit = (notfound)
postfix: dict_update: message_size_limit = 10240000
postfix: dict_lookup: hash_queue_depth = (notfound)
postfix: dict_update: hash_queue_depth = 1
postfix: dict_lookup: fork_attempts = (notfound)
postfix: dict_update: fork_attempts = 5
postfix: dict_lookup: deliver_lock_attempts = (notfound)
postfix: dict_update: deliver_lock_attempts = 20
postfix: dict_lookup: debug_peer_level = (notfound)
postfix: dict_update: debug_peer_level = 2
postfix: dict_lookup: fault_injection_code = (notfound)
postfix: dict_update: fault_injection_code = 0
postfix: dict_lookup: berkeley_db_create_buffer_size = (notfound)
postfix: dict_update: berkeley_db_create_buffer_size = 16777216
postfix: dict_lookup: berkeley_db_read_buffer_size = (notfound)
postfix: dict_update: berkeley_db_read_buffer_size = 131072
postfix: dict_lookup: header_size_limit = (notfound)
postfix: dict_update: header_size_limit = 102400
postfix: dict_lookup: header_address_token_limit = (notfound)
postfix: dict_update: header_address_token_limit = 10240
postfix: dict_lookup: mime_nesting_limit = (notfound)
postfix: dict_update: mime_nesting_limit = 100
postfix: dict_lookup: mime_boundary_length_limit = (notfound)
postfix: dict_update: mime_boundary_length_limit = 2048
postfix: dict_lookup: smtpd_tls_loglevel = (notfound)
postfix: dict_update: smtpd_tls_loglevel = 0
postfix: dict_lookup: smtp_tls_loglevel = (notfound)
postfix: dict_update: smtp_tls_loglevel = 0
postfix: dict_lookup: tls_daemon_random_bytes = (notfound)
postfix: dict_update: tls_daemon_random_bytes = 32
postfix: dict_lookup: disable_dns_lookups = (notfound)
postfix: dict_update: disable_dns_lookups = no
postfix: dict_lookup: soft_bounce = (notfound)
postfix: dict_update: soft_bounce = no
postfix: dict_lookup: owner_request_special = (notfound)
postfix: dict_update: owner_request_special = yes
postfix: dict_lookup: strict_8bitmime = (notfound)
postfix: dict_update: strict_8bitmime = no
postfix: dict_lookup: strict_7bit_headers = (notfound)
postfix: dict_update: strict_7bit_headers = no
postfix: dict_lookup: strict_8bitmime_body = (notfound)
postfix: dict_update: strict_8bitmime_body = no
postfix: dict_lookup: strict_mime_encoding_domain = (notfound)
postfix: dict_update: strict_mime_encoding_domain = no
postfix: dict_lookup: disable_mime_input_processing = (notfound)
postfix: dict_update: disable_mime_input_processing = no
postfix: dict_lookup: disable_mime_output_conversion = (notfound)
postfix: dict_update: disable_mime_output_conversion = no
postfix: dict_lookup: address_verify_negative_cache = (notfound)
postfix: dict_update: address_verify_negative_cache = yes
postfix: dict_lookup: backwards_bounce_logfile_compatibility = (notfound)
postfix: dict_update: backwards_bounce_logfile_compatibility = yes
postfix: dict_lookup: helpful_warnings = (notfound)
postfix: dict_update: helpful_warnings = yes
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: dict_lookup: application_event_drain_time = (notfound)
postfix: dict_update: application_event_drain_time = 100s
postfix: dict_lookup: application_event_drain_time = 100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: dict_lookup: max_idle = (notfound)
postfix: dict_update: max_idle = 100s
postfix: dict_lookup: max_idle = 100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: dict_lookup: ipc_timeout = (notfound)
postfix: dict_update: ipc_timeout = 3600s
postfix: dict_lookup: ipc_timeout = 3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: dict_lookup: ipc_idle = (notfound)
postfix: dict_update: ipc_idle = 100s
postfix: dict_lookup: ipc_idle = 100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: mac_parse: 1000s
postfix: dict_eval: const  1000s
postfix: dict_lookup: ipc_ttl = (notfound)
postfix: dict_update: ipc_ttl = 1000s
postfix: dict_lookup: ipc_ttl = 1000s
postfix: mac_parse: 1000s
postfix: dict_eval: const  1000s
postfix: mac_parse: 10s
postfix: dict_eval: const  10s
postfix: dict_lookup: trigger_timeout = (notfound)
postfix: dict_update: trigger_timeout = 10s
postfix: dict_lookup: trigger_timeout = 10s
postfix: mac_parse: 10s
postfix: dict_eval: const  10s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: fork_delay = (notfound)
postfix: dict_update: fork_delay = 1s
postfix: dict_lookup: fork_delay = 1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: deliver_lock_delay = (notfound)
postfix: dict_update: deliver_lock_delay = 1s
postfix: dict_lookup: deliver_lock_delay = 1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: mac_parse: 500s
postfix: dict_eval: const  500s
postfix: dict_lookup: stale_lock_time = (notfound)
postfix: dict_update: stale_lock_time = 500s
postfix: dict_lookup: stale_lock_time = 500s
postfix: mac_parse: 500s
postfix: dict_eval: const  500s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: dict_lookup: smtpd_tls_session_cache_timeout = (notfound)
postfix: dict_update: smtpd_tls_session_cache_timeout = 3600s
postfix: dict_lookup: smtpd_tls_session_cache_timeout = 3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: dict_lookup: smtp_tls_session_cache_timeout = (notfound)
postfix: dict_update: smtp_tls_session_cache_timeout = 3600s
postfix: dict_lookup: smtp_tls_session_cache_timeout = 3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: mac_parse: 18000s
postfix: dict_eval: const  18000s
postfix: dict_lookup: daemon_timeout = (notfound)
postfix: dict_update: daemon_timeout = 18000s
postfix: dict_lookup: daemon_timeout = 18000s
postfix: mac_parse: 18000s
postfix: dict_eval: const  18000s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: in_flow_delay = (notfound)
postfix: dict_update: in_flow_delay = 1s
postfix: dict_lookup: in_flow_delay = 1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: mynetworks = 127.0.0.0/8
postfix: mac_parse: 127.0.0.0/8
postfix: dict_eval: const  127.0.0.0/8
postfix: inet_addr_list_append: 127.0.0.1
postfix: inet_addr_list_append: 255.0.0.0
postfix: inet_addr_list_append: 192.168.1.105
postfix: inet_addr_list_append: 255.255.255.0
postfix: inet_addr_local: configured 2 IPv4 addresses
postfix: dict_update: process_id = 5702
postfix: dict_lookup: sendmail_path = (notfound)
postfix: mac_parse: /usr/sbin/sendmail
postfix: dict_eval: const  /usr/sbin/sendmail
postfix: dict_update: sendmail_path = /usr/sbin/sendmail
postfix: dict_lookup: mailq_path = (notfound)
postfix: mac_parse: /usr/bin/mailq
postfix: dict_eval: const  /usr/bin/mailq
postfix: dict_update: mailq_path = /usr/bin/mailq
postfix: dict_lookup: newaliases_path = (notfound)
postfix: mac_parse: /usr/bin/newaliases
postfix: dict_eval: const  /usr/bin/newaliases
postfix: dict_update: newaliases_path = /usr/bin/newaliases
postfix: dict_lookup: manpage_directory = (notfound)
postfix: mac_parse: /usr/share/man
postfix: dict_eval: const  /usr/share/man
postfix: dict_update: manpage_directory = /usr/share/man
postfix: dict_lookup: sample_directory = (notfound)
postfix: mac_parse: /usr/share/doc/postfix/examples
postfix: dict_eval: const  /usr/share/doc/postfix/examples
postfix: dict_update: sample_directory = /usr/share/doc/postfix/examples
postfix: dict_lookup: readme_directory = (notfound)
postfix: mac_parse: /usr/share/doc/postfix
postfix: dict_eval: const  /usr/share/doc/postfix
postfix: dict_update: readme_directory = /usr/share/doc/postfix
postfix: dict_lookup: html_directory = (notfound)
postfix: mac_parse: no
postfix: dict_eval: const  no
postfix: dict_update: html_directory = no
postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)

Calv

---

### Post by ape on 2006-09-15
Doh!  My bad.  command should have been:

  ```
/usr/sbin/postfix -vvv start
```

Sorry about that.  Can you post the output again from this...:(

---

### Post by calvinthomas on 2006-09-15
LOL, no problem, wouldn't run without superuser priveleges so with it I get:

postfix: dict_register: mail_dict 1
postfix: dict_update: config_directory = /etc/postfix
postfix: vstream_buf_get_ready: fd 4 got 1191
postfix: dict_update: smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
postfix: dict_update: biff = no
postfix: dict_update: append_dot_mydomain = no
postfix: dict_update: smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: dict_update: smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
postfix: dict_update: smtpd_use_tls = yes
postfix: dict_update: smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
postfix: dict_update: smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
postfix: dict_update: myhostname = localhost
postfix: dict_update: alias_maps = hash:/etc/aliases
postfix: dict_update: alias_database = hash:/etc/aliases
postfix: dict_update: mydestination = localhost, localhost.localdomain, , localhost
postfix: dict_update: relayhost = 
postfix: dict_update: mynetworks = 127.0.0.0/8
postfix: dict_update: mailbox_command = procmail -a "$EXTENSION"
postfix: dict_update: mailbox_size_limit = 0
postfix: dict_update: recipient_delimiter = +
postfix: dict_update: inet_interfaces = all
postfix: vstream_buf_get_ready: fd 4 got 318
postfix: dict_lookup: syslog_facility = (notfound)
postfix: mac_parse: mail
postfix: dict_eval: const  mail
postfix: dict_update: syslog_facility = mail
postfix: dict_lookup: inet_protocols = (notfound)
postfix: mac_parse: ipv4
postfix: dict_eval: const  ipv4
postfix: dict_update: inet_protocols = ipv4
postfix: name_mask: ipv4
postfix: dict_lookup: myhostname = localhost
postfix: mac_parse: localhost
postfix: dict_eval: const  localhost
postfix: dict_lookup: mydomain = (notfound)
postfix: mac_parse: localhost
postfix: dict_eval: const  localhost
postfix: dict_update: mydomain = localhost
postfix: dict_lookup: mail_name = (notfound)
postfix: mac_parse: Postfix
postfix: dict_eval: const  Postfix
postfix: dict_update: mail_name = Postfix
postfix: dict_lookup: syslog_name = (notfound)
postfix: mac_parse: postfix
postfix: dict_eval: const  postfix
postfix: dict_update: syslog_name = postfix
postfix: dict_lookup: mail_owner = (notfound)
postfix: mac_parse: postfix
postfix: dict_eval: const  postfix
postfix: dict_update: mail_owner = postfix
postfix: dict_lookup: setgid_group = (notfound)
postfix: mac_parse: postdrop
postfix: dict_eval: const  postdrop
postfix: dict_update: setgid_group = postdrop
postfix: dict_lookup: mydestination = localhost, localhost.localdomain, , localhost
postfix: mac_parse: localhost, localhost.localdomain, , localhost
postfix: dict_eval: const  localhost, localhost.localdomain, , localhost
postfix: dict_lookup: myorigin = (notfound)
postfix: mac_parse: $myhostname
postfix: dict_lookup: myhostname = localhost
postfix: mac_parse: localhost
postfix: dict_eval: expand $myhostname -> localhost
postfix: dict_update: myorigin = localhost
postfix: dict_lookup: relayhost = 
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_lookup: daemon_directory = (notfound)
postfix: mac_parse: /usr/lib/postfix
postfix: dict_eval: const  /usr/lib/postfix
postfix: dict_update: daemon_directory = /usr/lib/postfix
postfix: dict_lookup: command_directory = (notfound)
postfix: mac_parse: /usr/sbin
postfix: dict_eval: const  /usr/sbin
postfix: dict_update: command_directory = /usr/sbin
postfix: dict_lookup: queue_directory = (notfound)
postfix: mac_parse: /var/spool/postfix
postfix: dict_eval: const  /var/spool/postfix
postfix: dict_update: queue_directory = /var/spool/postfix
postfix: dict_lookup: process_id_directory = (notfound)
postfix: mac_parse: pid
postfix: dict_eval: const  pid
postfix: dict_update: process_id_directory = pid
postfix: dict_lookup: inet_interfaces = all
postfix: mac_parse: all
postfix: dict_eval: const  all
postfix: dict_lookup: proxy_interfaces = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: proxy_interfaces = 
postfix: dict_lookup: double_bounce_sender = (notfound)
postfix: mac_parse: double-bounce
postfix: dict_eval: const  double-bounce
postfix: dict_update: double_bounce_sender = double-bounce
postfix: dict_lookup: default_privs = (notfound)
postfix: mac_parse: nobody
postfix: dict_eval: const  nobody
postfix: dict_update: default_privs = nobody
postfix: dict_lookup: alias_database = hash:/etc/aliases
postfix: mac_parse: hash:/etc/aliases
postfix: dict_eval: const  hash:/etc/aliases
postfix: dict_lookup: mail_release_date = (notfound)
postfix: mac_parse: 20060405
postfix: dict_eval: const  20060405
postfix: dict_update: mail_release_date = 20060405
postfix: dict_lookup: mail_version = (notfound)
postfix: mac_parse: 2.2.10
postfix: dict_eval: const  2.2.10
postfix: dict_update: mail_version = 2.2.10
postfix: dict_lookup: default_database_type = (notfound)
postfix: mac_parse: hash
postfix: dict_eval: const  hash
postfix: dict_update: default_database_type = hash
postfix: dict_lookup: hash_queue_names = (notfound)
postfix: mac_parse: deferred, defer
postfix: dict_eval: const  deferred, defer
postfix: dict_update: hash_queue_names = deferred, defer
postfix: dict_lookup: recipient_delimiter = +
postfix: mac_parse: +
postfix: dict_eval: const  +
postfix: dict_lookup: relay_domains = (notfound)
postfix: mac_parse: $mydestination
postfix: dict_lookup: mydestination = localhost, localhost.localdomain, , localhost
postfix: mac_parse: localhost, localhost.localdomain, , localhost
postfix: dict_eval: expand $mydestination -> localhost, localhost.localdomain, , localhost
postfix: dict_update: relay_domains = localhost, localhost.localdomain, , localhost
postfix: dict_lookup: fast_flush_domains = (notfound)
postfix: mac_parse: $relay_domains
postfix: dict_lookup: relay_domains = localhost, localhost.localdomain, , localhost
postfix: mac_parse: localhost, localhost.localdomain, , localhost
postfix: dict_eval: expand $relay_domains -> localhost, localhost.localdomain, , localhost
postfix: dict_update: fast_flush_domains = localhost, localhost.localdomain, , localhost
postfix: dict_lookup: export_environment = (notfound)
postfix: mac_parse: TZ MAIL_CONFIG
postfix: dict_eval: const  TZ MAIL_CONFIG
postfix: dict_update: export_environment = TZ MAIL_CONFIG
postfix: dict_lookup: import_environment = (notfound)
postfix: mac_parse: MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
postfix: dict_eval: const  MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
postfix: dict_update: import_environment = MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY
postfix: dict_lookup: mynetworks_style = (notfound)
postfix: mac_parse: subnet
postfix: dict_eval: const  subnet
postfix: dict_update: mynetworks_style = subnet
postfix: dict_lookup: debug_peer_list = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: debug_peer_list = 
postfix: dict_lookup: default_verp_delimiters = (notfound)
postfix: mac_parse: +=
postfix: dict_eval: const  +=
postfix: dict_update: default_verp_delimiters = +=
postfix: dict_lookup: verp_delimiter_filter = (notfound)
postfix: mac_parse: -=+
postfix: dict_eval: const  -=+
postfix: dict_update: verp_delimiter_filter = -=+
postfix: dict_lookup: parent_domain_matches_subdomains = (notfound)
postfix: mac_parse: debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
postfix: dict_eval: const  debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
postfix: dict_update: parent_domain_matches_subdomains = debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
postfix: dict_lookup: alternate_config_directories = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: alternate_config_directories = 
postfix: dict_lookup: bounce_service_name = (notfound)
postfix: mac_parse: bounce
postfix: dict_eval: const  bounce
postfix: dict_update: bounce_service_name = bounce
postfix: dict_lookup: cleanup_service_name = (notfound)
postfix: mac_parse: cleanup
postfix: dict_eval: const  cleanup
postfix: dict_update: cleanup_service_name = cleanup
postfix: dict_lookup: defer_service_name = (notfound)
postfix: mac_parse: defer
postfix: dict_eval: const  defer
postfix: dict_update: defer_service_name = defer
postfix: dict_lookup: pickup_service_name = (notfound)
postfix: mac_parse: pickup
postfix: dict_eval: const  pickup
postfix: dict_update: pickup_service_name = pickup
postfix: dict_lookup: queue_service_name = (notfound)
postfix: mac_parse: qmgr
postfix: dict_eval: const  qmgr
postfix: dict_update: queue_service_name = qmgr
postfix: dict_lookup: rewrite_service_name = (notfound)
postfix: mac_parse: rewrite
postfix: dict_eval: const  rewrite
postfix: dict_update: rewrite_service_name = rewrite
postfix: dict_lookup: showq_service_name = (notfound)
postfix: mac_parse: showq
postfix: dict_eval: const  showq
postfix: dict_update: showq_service_name = showq
postfix: dict_lookup: error_service_name = (notfound)
postfix: mac_parse: error
postfix: dict_eval: const  error
postfix: dict_update: error_service_name = error
postfix: dict_lookup: flush_service_name = (notfound)
postfix: mac_parse: flush
postfix: dict_eval: const  flush
postfix: dict_update: flush_service_name = flush
postfix: dict_lookup: address_verify_service_name = (notfound)
postfix: mac_parse: verify
postfix: dict_eval: const  verify
postfix: dict_update: address_verify_service_name = verify
postfix: dict_lookup: trace_service_name = (notfound)
postfix: mac_parse: trace
postfix: dict_eval: const  trace
postfix: dict_update: trace_service_name = trace
postfix: dict_lookup: tls_random_exchange_name = (notfound)
postfix: mac_parse: ${config_directory}/prng_exch
postfix: dict_lookup: config_directory = /etc/postfix
postfix: mac_parse: /etc/postfix
postfix: dict_eval: expand ${config_directory}/prng_exch -> /etc/postfix/prng_exch
postfix: dict_update: tls_random_exchange_name = /etc/postfix/prng_exch
postfix: dict_lookup: smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: mac_parse: /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: dict_eval: const  /etc/ssl/certs/ssl-cert-snakeoil.pem
postfix: dict_lookup: smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
postfix: mac_parse: /etc/ssl/private/ssl-cert-snakeoil.key
postfix: dict_eval: const  /etc/ssl/private/ssl-cert-snakeoil.key
postfix: dict_lookup: smtpd_tls_dcert_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_dcert_file = 
postfix: dict_lookup: smtpd_tls_dkey_file = (notfound)
postfix: mac_parse: $smtpd_tls_dcert_file
postfix: dict_lookup: smtpd_tls_dcert_file = 
postfix: dict_eval: expand $smtpd_tls_dcert_file -> 
postfix: dict_update: smtpd_tls_dkey_file = 
postfix: dict_lookup: smtpd_tls_CAfile = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_CAfile = 
postfix: dict_lookup: smtpd_tls_CApath = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_CApath = 
postfix: dict_lookup: smtpd_tls_cipherlist = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_cipherlist = 
postfix: dict_lookup: smtpd_tls_dh512_param_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_dh512_param_file = 
postfix: dict_lookup: smtpd_tls_dh1024_param_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtpd_tls_dh1024_param_file = 
postfix: dict_lookup: smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
postfix: mac_parse: btree:${queue_directory}/smtpd_scache
postfix: dict_lookup: queue_directory = /var/spool/postfix
postfix: mac_parse: /var/spool/postfix
postfix: dict_eval: expand btree:${queue_directory}/smtpd_scache -> btree:/var/spool/postfix/smtpd_scache
postfix: dict_lookup: smtp_tls_cert_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_cert_file = 
postfix: dict_lookup: smtp_tls_key_file = (notfound)
postfix: mac_parse: $smtp_tls_cert_file
postfix: dict_lookup: smtp_tls_cert_file = 
postfix: dict_eval: expand $smtp_tls_cert_file -> 
postfix: dict_update: smtp_tls_key_file = 
postfix: dict_lookup: smtp_tls_dcert_file = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_dcert_file = 
postfix: dict_lookup: smtp_tls_dkey_file = (notfound)
postfix: mac_parse: $smtp_tls_dcert_file
postfix: dict_lookup: smtp_tls_dcert_file = 
postfix: dict_eval: expand $smtp_tls_dcert_file -> 
postfix: dict_update: smtp_tls_dkey_file = 
postfix: dict_lookup: smtp_tls_CAfile = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_CAfile = 
postfix: dict_lookup: smtp_tls_CApath = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_CApath = 
postfix: dict_lookup: smtp_tls_cipherlist = (notfound)
postfix: mac_parse: 
postfix: dict_eval: const  
postfix: dict_update: smtp_tls_cipherlist = 
postfix: dict_lookup: smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
postfix: mac_parse: btree:${queue_directory}/smtp_scache
postfix: dict_lookup: queue_directory = /var/spool/postfix
postfix: mac_parse: /var/spool/postfix
postfix: dict_eval: expand btree:${queue_directory}/smtp_scache -> btree:/var/spool/postfix/smtp_scache
postfix: dict_lookup: max_use = (notfound)
postfix: dict_update: max_use = 100
postfix: dict_lookup: dont_remove = (notfound)
postfix: dict_update: dont_remove = 0
postfix: dict_lookup: line_length_limit = (notfound)
postfix: dict_update: line_length_limit = 2048
postfix: dict_lookup: message_size_limit = (notfound)
postfix: dict_update: message_size_limit = 10240000
postfix: dict_lookup: hash_queue_depth = (notfound)
postfix: dict_update: hash_queue_depth = 1
postfix: dict_lookup: fork_attempts = (notfound)
postfix: dict_update: fork_attempts = 5
postfix: dict_lookup: deliver_lock_attempts = (notfound)
postfix: dict_update: deliver_lock_attempts = 20
postfix: dict_lookup: debug_peer_level = (notfound)
postfix: dict_update: debug_peer_level = 2
postfix: dict_lookup: fault_injection_code = (notfound)
postfix: dict_update: fault_injection_code = 0
postfix: dict_lookup: berkeley_db_create_buffer_size = (notfound)
postfix: dict_update: berkeley_db_create_buffer_size = 16777216
postfix: dict_lookup: berkeley_db_read_buffer_size = (notfound)
postfix: dict_update: berkeley_db_read_buffer_size = 131072
postfix: dict_lookup: header_size_limit = (notfound)
postfix: dict_update: header_size_limit = 102400
postfix: dict_lookup: header_address_token_limit = (notfound)
postfix: dict_update: header_address_token_limit = 10240
postfix: dict_lookup: mime_nesting_limit = (notfound)
postfix: dict_update: mime_nesting_limit = 100
postfix: dict_lookup: mime_boundary_length_limit = (notfound)
postfix: dict_update: mime_boundary_length_limit = 2048
postfix: dict_lookup: smtpd_tls_loglevel = (notfound)
postfix: dict_update: smtpd_tls_loglevel = 0
postfix: dict_lookup: smtp_tls_loglevel = (notfound)
postfix: dict_update: smtp_tls_loglevel = 0
postfix: dict_lookup: tls_daemon_random_bytes = (notfound)
postfix: dict_update: tls_daemon_random_bytes = 32
postfix: dict_lookup: disable_dns_lookups = (notfound)
postfix: dict_update: disable_dns_lookups = no
postfix: dict_lookup: soft_bounce = (notfound)
postfix: dict_update: soft_bounce = no
postfix: dict_lookup: owner_request_special = (notfound)
postfix: dict_update: owner_request_special = yes
postfix: dict_lookup: strict_8bitmime = (notfound)
postfix: dict_update: strict_8bitmime = no
postfix: dict_lookup: strict_7bit_headers = (notfound)
postfix: dict_update: strict_7bit_headers = no
postfix: dict_lookup: strict_8bitmime_body = (notfound)
postfix: dict_update: strict_8bitmime_body = no
postfix: dict_lookup: strict_mime_encoding_domain = (notfound)
postfix: dict_update: strict_mime_encoding_domain = no
postfix: dict_lookup: disable_mime_input_processing = (notfound)
postfix: dict_update: disable_mime_input_processing = no
postfix: dict_lookup: disable_mime_output_conversion = (notfound)
postfix: dict_update: disable_mime_output_conversion = no
postfix: dict_lookup: address_verify_negative_cache = (notfound)
postfix: dict_update: address_verify_negative_cache = yes
postfix: dict_lookup: backwards_bounce_logfile_compatibility = (notfound)
postfix: dict_update: backwards_bounce_logfile_compatibility = yes
postfix: dict_lookup: helpful_warnings = (notfound)
postfix: dict_update: helpful_warnings = yes
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: dict_lookup: application_event_drain_time = (notfound)
postfix: dict_update: application_event_drain_time = 100s
postfix: dict_lookup: application_event_drain_time = 100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: dict_lookup: max_idle = (notfound)
postfix: dict_update: max_idle = 100s
postfix: dict_lookup: max_idle = 100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: dict_lookup: ipc_timeout = (notfound)
postfix: dict_update: ipc_timeout = 3600s
postfix: dict_lookup: ipc_timeout = 3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: dict_lookup: ipc_idle = (notfound)
postfix: dict_update: ipc_idle = 100s
postfix: dict_lookup: ipc_idle = 100s
postfix: mac_parse: 100s
postfix: dict_eval: const  100s
postfix: mac_parse: 1000s
postfix: dict_eval: const  1000s
postfix: dict_lookup: ipc_ttl = (notfound)
postfix: dict_update: ipc_ttl = 1000s
postfix: dict_lookup: ipc_ttl = 1000s
postfix: mac_parse: 1000s
postfix: dict_eval: const  1000s
postfix: mac_parse: 10s
postfix: dict_eval: const  10s
postfix: dict_lookup: trigger_timeout = (notfound)
postfix: dict_update: trigger_timeout = 10s
postfix: dict_lookup: trigger_timeout = 10s
postfix: mac_parse: 10s
postfix: dict_eval: const  10s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: fork_delay = (notfound)
postfix: dict_update: fork_delay = 1s
postfix: dict_lookup: fork_delay = 1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: deliver_lock_delay = (notfound)
postfix: dict_update: deliver_lock_delay = 1s
postfix: dict_lookup: deliver_lock_delay = 1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: mac_parse: 500s
postfix: dict_eval: const  500s
postfix: dict_lookup: stale_lock_time = (notfound)
postfix: dict_update: stale_lock_time = 500s
postfix: dict_lookup: stale_lock_time = 500s
postfix: mac_parse: 500s
postfix: dict_eval: const  500s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: dict_lookup: smtpd_tls_session_cache_timeout = (notfound)
postfix: dict_update: smtpd_tls_session_cache_timeout = 3600s
postfix: dict_lookup: smtpd_tls_session_cache_timeout = 3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: dict_lookup: smtp_tls_session_cache_timeout = (notfound)
postfix: dict_update: smtp_tls_session_cache_timeout = 3600s
postfix: dict_lookup: smtp_tls_session_cache_timeout = 3600s
postfix: mac_parse: 3600s
postfix: dict_eval: const  3600s
postfix: mac_parse: 18000s
postfix: dict_eval: const  18000s
postfix: dict_lookup: daemon_timeout = (notfound)
postfix: dict_update: daemon_timeout = 18000s
postfix: dict_lookup: daemon_timeout = 18000s
postfix: mac_parse: 18000s
postfix: dict_eval: const  18000s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: in_flow_delay = (notfound)
postfix: dict_update: in_flow_delay = 1s
postfix: dict_lookup: in_flow_delay = 1s
postfix: mac_parse: 1s
postfix: dict_eval: const  1s
postfix: dict_lookup: mynetworks = 127.0.0.0/8
postfix: mac_parse: 127.0.0.0/8
postfix: dict_eval: const  127.0.0.0/8
postfix: inet_addr_list_append: 127.0.0.1
postfix: inet_addr_list_append: 255.0.0.0
postfix: inet_addr_list_append: 192.168.1.105
postfix: inet_addr_list_append: 255.255.255.0
postfix: inet_addr_local: configured 2 IPv4 addresses
postfix: dict_update: process_id = 6080
postfix: dict_lookup: sendmail_path = (notfound)
postfix: mac_parse: /usr/sbin/sendmail
postfix: dict_eval: const  /usr/sbin/sendmail
postfix: dict_update: sendmail_path = /usr/sbin/sendmail
postfix: dict_lookup: mailq_path = (notfound)
postfix: mac_parse: /usr/bin/mailq
postfix: dict_eval: const  /usr/bin/mailq
postfix: dict_update: mailq_path = /usr/bin/mailq
postfix: dict_lookup: newaliases_path = (notfound)
postfix: mac_parse: /usr/bin/newaliases
postfix: dict_eval: const  /usr/bin/newaliases
postfix: dict_update: newaliases_path = /usr/bin/newaliases
postfix: dict_lookup: manpage_directory = (notfound)
postfix: mac_parse: /usr/share/man
postfix: dict_eval: const  /usr/share/man
postfix: dict_update: manpage_directory = /usr/share/man
postfix: dict_lookup: sample_directory = (notfound)
postfix: mac_parse: /usr/share/doc/postfix/examples
postfix: dict_eval: const  /usr/share/doc/postfix/examples
postfix: dict_update: sample_directory = /usr/share/doc/postfix/examples
postfix: dict_lookup: readme_directory = (notfound)
postfix: mac_parse: /usr/share/doc/postfix
postfix: dict_eval: const  /usr/share/doc/postfix
postfix: dict_update: readme_directory = /usr/share/doc/postfix
postfix: dict_lookup: html_directory = (notfound)
postfix: mac_parse: no
postfix: dict_eval: const  no
postfix: dict_update: html_directory = no
calvin@calvin-laptop:~$

---

### Post by ape on 2006-09-17
Okay, don't see any errors that jump out at me.  Can you post the output (postfix.out file) of the following command:

   ```
sudo strace -o ~/postfix.out /usr/sbin/postfix start

```

---

