---
title: "How to run app. with wine that needs a DB server"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by xeo_pt on 2007-01-05
I have a application in Delphi that needs a database server in this case Firebird, how can I run the DB server as a service in order my application can work?

I install the server in wine but my app doesn't work.

thank you in advance.

---

### Post by benow on 2007-01-22
are you trying to run the dephi app under wine?  It will probably fail, as delphi's library dependancies are quite steep.  If you have the source, try kylix.  Otherwise, run in windows or windows in vmware (etc).  apt-get install firebird2 to get firebird going under ubuntu... it should set itself up to come up on boot.

---

### Post by mariuz on 2007-06-05
you can use these guides if you need to know how to work with firebird libraries under wine 

[http://www.osfinancials.org/mediawiki/index.php/Linux_Client_Eng_Install_manual](http://www.osfinancials.org/mediawiki/index.php/Linux_Client_Eng_Install_manual)

[http://www.ibexpert.com/download/using_ibexpert_with_linux_and_wine.pdf](http://www.ibexpert.com/download/using_ibexpert_with_linux_and_wine.pdf)

---

