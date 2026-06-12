---
title: "your NAGIOS setup..."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2007-07-17
just wondering how you use nagios... i am monitoring 2 servers via http_check and ping...  i have my alerting using an external smtp and it is working great...

took some tweaking - but now that it is working - it is great...  I highly recommend it...

just curiouis how you are using it... now that i have the hang of it i think i am going to monitor smtp, imap and ftp on my boxes as well...

---

### Post by upbeat.linux on 2007-07-25
I use Nagios in my work environment to monitor a whole bunch of services/boxes:

1. Exchange SMTP, IIS, etc
2. Server 2003 domain controllers (DNS, DHCP, AD)
3. Linux boxes - RH EL 3 & 4, Ubuntu Server 6.10 - httpd, mysql, samba
4. Backup Exec services
6. SQL Server 
7. Printers (and their wireless bridgeS)
8. WAPs
9. availability of firewall, routers, and switches
10. VoIP system

You've probably seen that fun ad on many tech sites about using Nagios and Splunk together. That's exactly what I'm doing although I don't currently have the funding to purchase the unrestricted license for Splunk.

---

