---
title: "Ubuntu Server - Enabling CGI"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by jert on 2007-04-24
Greetings all.

Can someone point me towards a step by step howto on enabling CGI in a specific directory (outside of /usr/lib/cgi-bin)?

I've managed to make cgi scripts execute in the /usr/lib/cgi-bin directory, so I know I've got all the required components installed correctly.  However, the script can't properly access its .css file and image components (in a sub-directory under /usr/lib/cgi-bin), which means it does not display properly.

I've used a simlink in my web root (/var/www) to link to the folder containing the script (/usr/share/script/), and tried to enable ExecCGI on that directory using .htaccess files, Directory statements in apache2.conf, and File statements in apache2.conf ... but for some reason I have not been able to stumble onto the magical combination that will make things work.  

I know that I've got permissions problems which are preventing proper operation ... but I've changed the file/group ownership to www-data for everything in the directory, and the scripts all have owner execution rights.  

Can anyone point me towards a link, how-to site, or troubleshooting document which can help step me through resolving these issues?

Using Ubuntu Server 7.04, but installed the full ubuntu-desktop package after the initial server build.


Thanks in advance!

---

### Post by hacme on 2007-10-12
I'm new to Ubuntu Server as well and am enjoying this great distro. This link may help you:

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

It discusses creating new sites and configuring a cgi-bin directory.

Take care.

---

