---
title: "Internal Server Error"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by callgary on 2008-02-28
PHP scripts placed in the /usr/lib/cgi-bin folder generate error 500 Internal Server Error.  The server encountered an internal error or misconfiguration ...........

The same script runs OK from a folder under www directory.

should I move my cgi-bin folder to www, if so, how????

how should cgi-bin be setup and configured????

Thanks
Gary

---

### Post by jfinkels on 2008-02-29
I don't know much about cgi, but have you considered installing the PHP Apache module? To do so, type in the terminal:```
sudo aptitude install libapache2-mod-php
```This is the method PHP is usually installed on the LAMP stack, I believe... This way, any "*.php" files that apache serves will be interpreted by the PHP interpreter and rendered correctly without any CGI.

---

### Post by callgary on 2008-02-29
I installed PHP5 using synaptic package manager.  I installed everything that had a ubuntu symbol next to it that began with PHP5.

Gary

---

### Post by Teber on 2008-02-29
internal server errors may be caused by incorrect permissions. try chmodding the scripts to 755, if memory serves...

cgi-bin should always be 711, but that would certainly correct on your server. 

for correct permissions consult the manual?

---

### Post by Teber on 2008-02-29
ran into that one installing perl scripts. i know there are similar requirements for php.

---

