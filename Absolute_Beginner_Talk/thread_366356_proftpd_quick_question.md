---
title: "proftpd quick question"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by ilyash on 2007-02-20
I would like to give my user "site" permissions to upload to /usr/local/tomcat/webapps/ROOT

site's home is /home/site and I can upload there fine.
I tried to make a symbolic link... ln-s /usr/local/tomcat/webapps/ROOT ROOT in the home dir.. but smart ftp doesnt see it.
When I access the ftp with windows explorer, it can see the shortcut.. but opens a new window:
[ftp://[my](ftp://[my) ip here]/ROOT
which says page cannot be displayed.

I did the following to give site permissions:

```

<Directory /usr/local/tomcat/webapps/ROOT/*>
<Limit ALL>
AllowUser anthony
AllowUser ilya
AllowUser site
AllowUser alex
AllowUser theo
</Limit>
</Directory>

```

Thanks.

---

