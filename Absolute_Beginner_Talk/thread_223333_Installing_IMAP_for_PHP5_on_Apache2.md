---
title: "Installing IMAP for PHP5 on Apache2"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by studio24 on 2006-07-26
hi there
New to this forum. I'm trying to install the IMAP module for PHP and have located the "php-imap" package in the Package manager. However, it tells me I cannot install this package because it depends on: phpapi-20051025

After a search on Google, I see that this phpapi package is supported within libapache2-mod-php5 though obviously not the version I have installed (5.1.4-1.dotdeb.2). 

I tried forcing the version to 5.1.2-1ubuntu3.1 [security] but nothing happened in the package manager. 

Any suggestions? I need to use IMAP for FogBugz which I'm trying to install (commercial bug tracking software).

I'm using the latest stable version of ubuntu. If I go to Software Updates it states my system is currently up to date.

best wishes,
Simon

---

### Post by destro on 2006-07-26
install 
libc-client-dev - UW c-client library for mail protocols
libc-client2002edebian - UW c-client library for mail protocols

then try again, if still having issues, consider compiling php from source.  pretty easy to do.

---

### Post by studio24 on 2006-07-26
thanks, i've installed the recommended packages, but when I try to install php5-imap I still get:

Unresolveable dependancies
 Depends: phpapi-20051025

So if I install PHP from source should I uninstall it from the package manager first?

I've never actually installed from source before but I assume if I include the line --with-imap[=DIR] this will enable the IMAP modules for PHP. I have installed courier-imap installed so I assume the correct line is --with-imap=/usr/lib/courier

Does this sound correct?

thanks,
Simon

---

