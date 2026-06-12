---
title: "Newbie Help!!!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by djsky on 2008-02-09
I have Gutsy distro installed with Apache2, PHP5 and mySQL servers.  I created a test.php file to make sure php scripts are executing properly and it worked just fine.  However, every time I try to run a regular PHP script,  the server stalls.  In firefox, when I run a PHP script, it gets stuck on "waiting for www.myserver.com" and doesn't go anywhere else.  After that, any requests to other pages on the server get stuck on the same message.

I reinstalled Apache2 and PHP5 probably twice already to try to resolve this to no avail.  Is it something in php.ini or apache.conf that needs to be tweaked???  Please help.  I need to get my webserver up and running.


Thanks.

---

### Post by Kilz on 2008-02-09
In /etc/apache2/mods-enabled is there a php5.conf and a php5.load file? If not copy them over from the /etc/apache2/mods-available folder, then restart apache.

---

### Post by djsky on 2008-02-09
Yes there is.  Both files are there.  Any other suggestions???  Please!!!

---

### Post by djsky on 2008-02-09
Can someone please suggest what I should do???  I need to setup this webserver as soon as I can.

---

### Post by djsky on 2008-02-24
What I noticed is that every php script stalls the server during user registration.  For example I tried installing 3 different php auction scripts and they all get stuck when user is trying to register.

Does anyone have any suggestions???  Any at all???

---

### Post by Martje_001 on 2008-02-25
which packages did you install?

---

### Post by djsky on 2008-02-25
I have installed apache2 and php5 with the following mods enabled:

core mod_log_config mod_logio prefork http_core mod_so mod_alias mod_auth_basic mod_authn_file mod_authz_default mod_authz_groupfile mod_authz_host mod_authz_user mod_autoindex mod_cgi mod_dir mod_env mod_include mod_mime mod_negotiation mod_php5 mod_rewrite mod_setenvif mod_ssl mod_status mod_suexec

---

