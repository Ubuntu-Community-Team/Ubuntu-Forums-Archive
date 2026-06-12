---
title: "php -v doesnt work"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-04-07
Im trying to make sure i have the fast-CGI version of PHP installed. The **php -v **command does not work. Any other way to check? Synaptic just lists it as php-cgi...

---

### Post by WickedImp on 2006-04-07
Hi there,

never used the CGI version of php. Only the apache module (works fine, is secure and fast enough). But one thing I know for sure. The command php -v only works if you installed the CLI version of php (Command Line Interpreter). You should apt-get install php4-cgi.

Regards
Imp

---

