---
title: "Apache2 Perl Help"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by ielliott on 2006-11-01
Alright so i added the following the apache2.conf script

#<Directory /var/www/perl>
#  Options +execCGI
#  AddHandler cgi-script .cgi .pl
#</Directory>

Then i went to start apache and it failed.

 * Starting apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                                                         [fail]

So i comment out that above, and it still doesn't work.

Also if i delete it from the Apache2.conf its also still continues not to work.


I am just trying to get it so i can execute Perl in apache.

If i can be pointed in the right direction that would be great.

---

### Post by ielliott on 2006-11-01
Ok so i found my problem

i added

PerlModule Apache2 to perl.conf

so it caused the error.

Any thing i can do about this?

---

