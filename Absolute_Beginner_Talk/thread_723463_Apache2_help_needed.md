---
title: "Apache2 help needed"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by jon_shep on 2008-03-13
Hi everyone,

I'm having problems setting up authentication for my apache2 web server.  I have created the htpasswd and modified my httpd.conf file with the following :

<Directory "/var/www/jon">
        Options FollowSymLinks
        AllowOverride None

        AuthType Basic
        AuthName "Jon"
        AuthUserFile /etc/apache2/passwd/password
        Require valid-user
</Directory "/var/www/jon">

However when I try to restart apache2 it throws up the following error :

root@bigblack:/etc/apache2# /etc/init.d/apache2 reload
apache2: Syntax error on line 187 of /etc/apache2/apache2.conf: Syntax error on line 9 of /etc/apache2/httpd.conf: </Directory> directive missing closing '>'
   ...fail!
root@bigblack:/etc/apache2#

Can anyone shed some light where I'm going wong

Thanks

---

### Post by ViRMiN on 2008-03-13
Try your last line as:

</Directory>

---

### Post by lespaul_rentals on 2008-03-13
> **jon_shep said:**
> Hi everyone,

I'm having problems setting up authentication for my apache2 web server.  I have created the htpasswd and modified my httpd.conf file with the following :

<Directory "/var/www/jon">
        Options FollowSymLinks
        AllowOverride None

        AuthType Basic
        AuthName "Jon"
        AuthUserFile /etc/apache2/passwd/password
        Require valid-user
</Directory "/var/www/jon">

However when I try to restart apache2 it throws up the following error :

root@bigblack:/etc/apache2# /etc/init.d/apache2 reload
apache2: Syntax error on line 187 of /etc/apache2/apache2.conf: Syntax error on line 9 of /etc/apache2/httpd.conf: </Directory> directive missing closing '>'
   ...fail!
root@bigblack:/etc/apache2#

Can anyone shed some light where I'm going wong

Thanks

Are you making said changes to *httpd.conf*, or *apache2.conf*?  Ubuntu reads *apache2.conf*, while other distros such as Arch, Slackware, etc. read *httpd.conf*.

---

### Post by jon_shep on 2008-03-13
thanks!

Changing to </directory> has worked a treat!

Cheers
jonathan

---

