---
title: "Can't get past authentication in the CUPS admin interface"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-02-14
In /etc/cups/cupsd.conf, I have the following configurations:

```

SystemGroup lpadmin

<Location /jobs>
AuthType Basic
AuthClass User
</Location>


<Location /admin>
AuthType Basic
AuthClass System

Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

```

User 'peter' is a member of the group lpadmin.

However, when I tried to login with userid 'peter' and his password, the authentication window vanishes and reappears.

What do I need to configure to get the authentication successful?

Btw, what does 'User' in 'AuthClass User' means?

Thanks in advance !

---

### Post by joft on 2006-02-15
Hi,

I think, the problem is, that in ubuntu the cups webinterface's administration part is disabled.

Have a look at this thread:
[http://ubuntuforums.org/showpost.php?p=716188&postcount=2](http://ubuntuforums.org/showpost.php?p=716188&postcount=2)

There somebody posted a link to this page:
[http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/](http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/)

---

