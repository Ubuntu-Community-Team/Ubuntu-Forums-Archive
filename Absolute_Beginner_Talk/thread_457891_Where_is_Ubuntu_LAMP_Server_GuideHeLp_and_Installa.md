---
title: "Where is Ubuntu LAMP Server Guide/HeLp and Installation notes?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Usucktu on 2007-05-29
for example like this (like for WAMP)
[http://www.devside.net/download/wd-guide/](http://www.devside.net/download/wd-guide/)

There exist of course a  link on [www.ubuntu.com](www.ubuntu.com) to download server/desktop   but there is NO ANY GUIDES to help install web server/forums etc

---

### Post by 1/0 on 2007-05-29
Well, the good ol' Google found me plenty of guides. here are the top three I found:

[http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html)
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

---

### Post by esoterica on 2007-05-29
To get a LAMP install on your Ubuntu desktop I can tell you first hand by doing so myself these documentation files will get you there. I followed them using "aptitude install ..." as my "Any Method" they mention and it has me a LAMP server up and running.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It could probably be done easier using the synaptic installer thing, though I never seen an option anywhere in all those thousands of files for mysql-server, which is why I instead just used the terminal and ran aptitude install for each of the applications listed in that documentation I linked to.

I'm about ready yo give up on trying to do things the Ubuntu way though and uninstall all of it I did this way to recompile my entire working LAMP install on the 7.04 desktop by following these instructions instead and compiling it all from source code.

I think is is probably a much better way to go...

[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

That step by step tutorial covers installing Apache2, there are links there though for a complete and very secure LAMP install.

---

### Post by zvacet on 2007-05-29
**synaptic>edit>mark packages by task**

---

