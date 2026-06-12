---
title: "Set up a FTP server"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-21
I have a DynDNS account set up that I use for VNC and now I would like to turn my ubuntu box into a FTP server through DNS. If anyone has done this or if anyone knows how to do this please help me out.

---

### Post by tuxrtfm on 2006-10-21
Check out this thread for setting up the server:
"http://ubuntuforums.org/showthread.php?t=79588"

And here for dyndns configuration:
"http://doc.gwos.org/index.php/DapperGuide#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service"

Also if you want to setup more than ftp in the future check this out:
"http://www.howtoforge.com/perfect_setup_ubuntu_6.06"

> The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)

Version 1.0
Author: Falko Timme <ft [at] falkotimme [dot] com>
Last edited 06/03/2006

This is a detailed description about how to set up a Ubuntu 6.06 LTS (Dapper Drake) based server that offers all services needed by ISPs and hosters (web server (SSL-capable), mail server (with SMTP-AUTH and TLS!), DNS server, FTP server, MySQL server, POP3/IMAP, Quota, Firewall, etc.).

I will use the following software:

    * Web Server: Apache 2.0
    * Database Server: MySQL 5.0
    * Mail Server: Postfix
    * DNS Server: BIND9
    * FTP Server: proftpd
    * POP3/IMAP: I will use Maildir format and therefore install Courier-POP3/Courier-IMAP.
    * Webalizer for web site statistics

In the end you should have a system that works reliably, and if you like you can install the free webhosting control panel ISPConfig (i.e., ISPConfig runs on it out of the box).

---

