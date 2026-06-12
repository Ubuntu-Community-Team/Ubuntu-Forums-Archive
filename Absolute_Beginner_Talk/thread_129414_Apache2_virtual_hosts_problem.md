---
title: "Apache2 virtual hosts problem"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by lreyes6 on 2006-02-13
when i restart, start stop my apache2 service this message come's out
```

 * Forcing reload of web server  (Apache2)... 
[Mon Feb 13 16:52:55 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
[Mon Feb 13 16:52:55 2006] [warn] NameVirtualHost *:0 has no VirtualHosts

```

what that supposed to mean? is that an error? how do i fix it?

thanks

---

### Post by lreyes6 on 2006-02-14
I found the answer... the problem was that another application replace my virtualhost file... this is a good documentation in [ApacheFreaks]("http://www.apachefreaks.com/apache2/")

but the solution was this... in the file /etc/apache2/sites-availabe/default write this

```

<VirtualHost ip_address_from_server>
   ServerAdmin admin_em@il
   DocumentRoot /var/www
   ErrorLog /var/log/error_log
   CustomLog /var/log/access_log common
</VirtualHost>

cheers

```

---

