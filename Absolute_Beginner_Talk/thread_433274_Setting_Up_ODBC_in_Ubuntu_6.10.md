---
title: "Setting Up ODBC in Ubuntu 6.10"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by rrkano on 2007-05-04
I have Ubuntu 6.10 and I want to set up an ODBC Connection to a SQL Server/DB on my network. So, I want to host PHP Pages on the Ubuntu Server but I want to make use of an existing SQL Server on our network that's running on a Windows 2003 Server. Is this possible? 

Thanks

---

### Post by haricharan on 2007-05-04
install odbc extension for ```
sudo apt-get install php4-odbc
``` or ```
sudo apt-get install php5-odbc
``` depending on what version of php u have.....
and then follow this link [http://www.w3schools.com/php/php_db_odbc.asp](http://www.w3schools.com/php/php_db_odbc.asp)

---

### Post by rrkano on 2007-05-04
Thanks...

It said it was already installed. So, now I cannot find where to go set up  the ODBC DSN. Those instructions in the link you referred me to, don't say how to set up the DSN on the Ubuntu server. It looks like they're instructions for a Windows Server. 

Thanks

---

### Post by haricharan on 2007-05-04
see this it says u can use DSNless connections too [http://phplens.com/phpeverywhere/node/view/9](http://phplens.com/phpeverywhere/node/view/9)

---

