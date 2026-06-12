---
title: "Apache/PHP Help-Too many conflicting answers"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by boetheus on 2006-02-10
I tried to remove PHP5 and go to PHP4.  When I did that I got the dreaded httpd-php problem.  I have been searching the forum for the answers, but I see so many answers,  I believe I need to configure apache2 to handle PHP.  What is supposed to be in my httpd.conf file?  This is  the only thin that is in mine.
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

Lets assume that i have no special problems going on, what are the steps to make the two programs communicate?
What other files need to be changed because I think that I am missing some files?:confused:

---

### Post by boetheus on 2006-02-10
Okay, I fixed part of my problem.  I went back and installed apache 1.3. and the other needed components.  Now my site is starting to come back up.  I can not access my Joomla admin login.  It won't give me the login page.  Any solutions.

---

