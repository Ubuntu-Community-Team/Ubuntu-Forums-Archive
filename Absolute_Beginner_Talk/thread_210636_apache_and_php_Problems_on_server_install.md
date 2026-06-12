---
title: "apache and php Problems on server install"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by daddy3may2005 on 2006-07-07
Hi all-

  I am new to linux and ubuntu and am trying to get my machine to allow formmail to be sent.  Here is what I have done so far.

PHP & Perl are both installed.  I have the run chmod a=rx on the script.  I have read in many places not to place it in the cgi-bin folder so I have tried both.  I am still getting the follow error...

Forbidden
You don't have permission to access /js/formmail.cgi on this server.


--------------------------------------------------------------------------------

Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_perl/2.0.2 Perl/v5.8.7 

I have tried the cgi script * a php script.  Same problems...

PLEASE HELP

---

### Post by mgor on 2006-07-07
take a look in /etc/apache2/apache2.conf,
```
# To use CGI scripts outside /cgi-bin/:
#
#AddHandler cgi-script .cgi
```

uncomment the AddHandler line and restart apache. if it still dosen't work, make sure the script is owned by the user www-data (check for User in apache2.conf)
```
chown www-data formmail.cgi
```

---

### Post by daddy3may2005 on 2006-07-07
Thanks for the reply...

 I tried that and it gives me the same error... It has the exact same props as any other file in the directory I have it in and you can access those files.  Not sure where else to go with this one..

---

