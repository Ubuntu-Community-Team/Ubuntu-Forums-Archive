---
title: "HELP....I can't see a website (Apache)"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by ErikaCruz on 2005-10-17
I have been trying to set up an ERP SW named Arias in  my Apache webserver but it doesn't find my DocumentRoot


First
1.- I placed my Arias installation in /opt/lampp/htdocs/arias

Then I changed the Apache Configuration file in /opt/lampp/etc/httpd.conf
2. - DocumentRoot /opt/lampp/htdocs/arias
3. - Then make sure there was an index.php on the DirectoryIndex
DirectoryIndex index.php index.html index.html.var

However, anytime I tried to check my website [http://localhost/arias](http://localhost/arias) I receive a message saying

"Not Found

The requested URL /arias was not found on this server.
Apache/2.0.54 (Unix) mod_ssl/2.0.54 OpenSSL/0.9.8 PHP/5.0.4 DAV/2 mod_perl/2.0.1 Perl/v5.8.7 Server at localhost Port 80"

Please if anyone could help me I will appreciate it. I don't understand why it says not found if I already changed th DocumentRoot....

Thanks a lot...

---

### Post by tats on 2005-10-17
did you restart Apache after changing httpd.conf ?

---

