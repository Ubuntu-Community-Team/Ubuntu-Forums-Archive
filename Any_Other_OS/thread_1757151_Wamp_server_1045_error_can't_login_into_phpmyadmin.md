---
title: "Wamp server 1045 error can't login into phpmyadmin"
date: 2011-05-13
forum: Any Other OS
---

### Post by Krauser Joestar on 2011-05-13
Hello everyone 
 
 
My wamp server is working fine, i can access everything on it. However,  the people working in the network, then they type their username and  password at the phpmyadmin page, they can't acess it. 
 
The error is the infamous **#1045 error can't login into phpMYadmin#(it doesn't say anything about passwords or denied accesses, just what i wrote) **
 
 
I already configured the phpmyadmin.conf alias to allow the ip of the person that i'm testing this with, and still nothing. 
 
 
Alias /phpmyadmin "c:/wamp/apps/phpmyadmin3.3.9/"  
 
# to give access to phpmyadmin from outside  
# replace the lines 
# 
#        Order Deny,Allow 
#    Deny from all 
#    Allow from 127.0.0.1 
# 
# by 
# 
#        Order Allow,Deny  
#   Allow from all 
# 
 
<Directory "c:/wamp/apps/phpmyadmin3.3.9/"> 
    Options Indexes FollowSymLinks MultiViews 
    AllowOverride all 
        Order Deny,Allow 
    Deny from all 
    Allow from 127.0.0.1 
    Allow from 10.64.46.20 ---------------------> Mine
    Allow from 10.64.46.29 --------------------> My colleague's IP address.
    </Directory> 
 
 
 
I've search all over the internet and nothing. There are many solutions(even if in practice only 2 or 3 work) when the error is:

1045 error - access denied for user@blabla


But it's not the case here, and i can login just fine. 


Any ideas guys?

---

### Post by Krauser Joestar on 2011-05-13
Actually, the error is [B]#1045 Cannot log in to the MySQL server



[/B]I can login just fine but not my colleague[B] :(
[/B]

---

### Post by motang on 2013-02-15
Change the file content of c:\wamp\alias\phpmyadmin.conf to the following:

```
<Directory "c:/wamp/apps/phpmyadmin3.4.5/">
    Options Indexes FollowSymLinks MultiViews
    AllowOverride all
        Order Deny,Allow
        Allow from all
</Directory>
```

You most likely have ```
Deny from all
    Allow from 127.0.0.1
```, which was most likely caused when you made your WAMP server go online.

---

