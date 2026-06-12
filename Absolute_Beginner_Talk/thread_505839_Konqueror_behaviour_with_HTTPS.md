---
title: "Konqueror behaviour with HTTPS:"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by John Boy on 2007-07-20
Konqueror works well with most sites but when I go to a bank (ANZ) site which goes into HTTPS it stops/stalls without any error or indication of what it is waiting for. My login has been accepted and when I go to this site with IE it asks me if I wish to close a window and it goes into the HTTPS environment. With Konqueror I do not get the message about the window and there are no other tabs on to it. I can successfully visit other SSL sites so think the configuration for SSL 2 & 3 is OK. Have checked the configuration options and see nothing suspicious, How can I tell what is holding Konqueror up  or what it causing it a problem ?

              Thanks,

                         Slainte,

                                    John

---

### Post by w4ett on 2007-07-20
Is Java installed/enabled?

---

### Post by DBStevens on 2007-07-20
You might also want to have Konqueror lie about who it is.

The user agent string it is sending to the server may be confusing it.

---

### Post by John Boy on 2007-07-21
Java is enabled but I found that Java Script was not. When I enabled it things worked. Thanks for your help.

              John

---

