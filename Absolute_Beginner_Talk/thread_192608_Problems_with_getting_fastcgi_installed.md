---
title: "Problems with getting fastcgi installed"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2006-06-08
I am trying to get ruby on rails running on my system, but it is the part that deals with the fastcgi that is causing problems.

Here is the page that I am trying to follow to get everything setup
**[http://wiki.rubyonrails.com/rails/pages/HowtoSetupApacheWithFastCGIAndRubyBindings](http://wiki.rubyonrails.com/rails/pages/HowtoSetupApacheWithFastCGIAndRubyBindings)**

Everything seems to work up to step 12, and I try to start the apache server:
**/usr/local/apache2/bin/apachectl start**

I then get the error saying:
[B]chris@ubuntu:/usr/local/apache2$ bin/apachectl start
httpd: Syntax error on line 412 of /usr/local/apache2/conf/httpd.conf: Cannot load /usr/local/apache2/modules/mod_fcgid.so into server: /usr/local/apache2/modules/mod_fcgid.so: cannot open shared object file: No such file or directory[/B]

The files that is claims aren't there..well they aren't there, so is there something that I am missing?
[I]--EDIT
I should be a little clearer on this.  I am just a little confused to where these files were supposed to have been created during the setup process.
[/I]


Thanks for the help.

---

### Post by chris.olsen on 2006-06-09
Sorry I have to bump this one.  If I can get this working I can reduce my time at home  spent on Windows by at least 50% :)

---

