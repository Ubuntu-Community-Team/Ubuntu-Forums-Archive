---
title: "[SOLVED] apache problems"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by gleble on 2008-02-16
I had apache working properly but now if I enter [http://localhost/htdocs/solar.php](http://localhost/htdocs/solar.php) I get 500 Internal Server Error
Can anyone suggest why. Strangely [http://localhost/fdb.htm](http://localhost/fdb.htm) works.Where is fdb.htm being stored?  Where is the server error log?

*Apache/2.2.4  (Ubuntu) PHP/5.2.3-1 ubuntu6.3 Server at localhost Port 80*

---

### Post by gleble on 2008-02-16
[http://localhost/htdocs](http://localhost/htdocs) gives Index  of /htdocs but cicking a file gives the same error?

---

### Post by louieb on 2008-02-16
Just a shot in the dark. Apache2 running on Gutsy looks for  html in **/var/www **Might look for fdg.htm there.

The log files are in /var/log/apache2

---

### Post by siouzi on 2008-02-16
Look at the apache error log /var/log/apache2/(some filename with error, error.log?). It looks like the solar.php script can't be executed. The script contains errors or the permissions of the script file or the directory containing the script are wrong. Set permissions to: chmod 644 solar.php and chmod 755 htdocs.

---

### Post by gleble on 2008-02-16
Thanks var/www was what I was looking for.

---

