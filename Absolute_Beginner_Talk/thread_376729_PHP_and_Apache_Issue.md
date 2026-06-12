---
title: "PHP and Apache Issue"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by handyguy33 on 2007-03-05
Hi all. I received some updates on my server last week. Ever since, my website has been down. When I go to it in a browser, it asks me to open or save the file as an application. I've been scanning the forums and fiddling with this and that but still no joy. the last command i typed in was:  sudo /etc/init.d/apache2 start
I got the result:  * Starting apache 2.0 web server... Syntax error on line 8 of /etc/apache2/httpd.conf:
Cannot load /etc/apache2/libexec/libphp5.so into server: /etc/apache2/libexec/libphp5.so: cannot open shared object file: No such file or directory
                                                                         [fail]
My knowledge of PHP is non-existant (I inherited this server/website so had no hand in the creation of either).
Any help would be appreciated...

---

### Post by anaconda on 2007-03-05
so.. what have you got in /etc/apache2/httpd.conf  in and around line 8 ??

In my httpd.conf all lines are commented away (default)

---

### Post by handyguy33 on 2007-03-05
here's what my httpd.conf looks like:

AddType application/x-httpd-php .php# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

LoadModule php5_module libexec/libphp5.so

AddModule mod_php5.c

#
# PHP is an HTML-embedded scripting language which attempts to make it
# easy for developers to write dynamically generated webpages.
#

LoadModule php5_module modules/libphp5.so

#
# Cause the PHP interpreter to handle files with a .php extension.
#
AddHandler php5-script .php
AddType text/html .php

---

### Post by handyguy33 on 2007-03-05
Anybody?

---

### Post by annda on 2007-03-05
as far as i can tell you have two entries for libphp5.so

navigate you filesystem to /usr/lib/apache2/modules/ and see where the module actually is.

maybe you will need to comment out that first entry (it might be an older location or something, i'm a casual apache user myself.)

---

### Post by handyguy33 on 2007-03-06
Tried it. First uncommented one, saved and restarted apache, then replaced it and tried the same with the other. No joy. BTW, I looked for libphp5.so in etc, usr, and var sub folders and I don't see it anywhere. If that's the case, where do I find it and where do I put it?

---

