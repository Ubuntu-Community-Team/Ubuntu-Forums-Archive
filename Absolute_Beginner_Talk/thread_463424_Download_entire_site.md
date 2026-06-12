---
title: "Download entire site"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by IsKall on 2007-06-03
I am trying to download entire course site so I can have the materials with me even if I wont have access to the website.

so I am trying to do this in the terminal to download:

[HTML]
wget -r --no-parent http://username:password@www.somthing.com/courses/aaaaaaaa
[/HTML]

but I get this message:

[HTML]
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
[/HTML]

But I can login through the web browser, so this means that I have typed wrong.

---

### Post by FuturePast on 2007-06-03
```
$ man wget
...
--user=user
       --password=password
...

```

---

### Post by yabbadabbadont on 2007-06-03
Try using wget's "--user" and "--password" options to specify the user and password.  Note that it is two dashes before the words user and password.

Edit: Doh!  Too slow.  :D

---

