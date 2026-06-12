---
title: "need a good tutorial on linux permissions"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by huggy77 on 2006-11-29
looking for a good tutorial on linux permissions... On my test box i usually chmod 777 to get stuff to work - but i know this is HIGHLY INSECURE/STUPID... want to learn more...

basically want to give a specific group w/r access to a specific folder - need to know my options...

thanks in advance...

---

### Post by bodhi.zazen on 2006-11-29
> **huggy77 said:**
> looking for a good tutorial on linux permissions... On my test box i usually chmod 777 to get stuff to work - but i know this is HIGHLY INSECURE/STUPID... want to learn more...

basically want to give a specific group w/r access to a specific folder - need to know my options...

thanks in advance...

[Google serch](http://www.google.com/search?q=permissions+linux&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)

Google is a good place to start. The two first links are fine....

to answer your question:

```
chown user_name:group_name <directory>

chmod 770 <directory> 
```


will likely do....

---

### Post by John.Michael.Kane on 2006-11-29
[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)
[http://www.hostingmanual.net/other/permissions.shtml](http://www.hostingmanual.net/other/permissions.shtml)
[http://www.elated.com/articles/understanding-permissions/](http://www.elated.com/articles/understanding-permissions/)

---

### Post by huggy77 on 2006-11-29
thanks - i will check those out...

---

