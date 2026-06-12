---
title: "Web Server ?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by kozak on 2005-12-28
Is there any way to run a website off my computer with ubuntu ?
I've never done this before and don't know how.
So I was wondering if this is possible.

---

### Post by cwaldbieser on 2005-12-29
[QUOTE=kozak]Is there any way to run a website off my computer with ubuntu ?
I've never done this before and don't know how.
So I was wondering if this is possible.[/QUOTE]
Yes.  There are some hurdles to doing this.  For example, if you have a typical home user plan for your ISP, they probably have included some verbage that you are not allowed to run a high volume server.  Many ISPs provide you with some simple web space on their servers as part of your package, however.

If you are connecting from behind a router, you will have to forward port 80 to your Ubuntu PC.

Finally, your ISP probably assigns your IP address dynamically.  There are free services you can sign up for that will point a domain name to your current IP address.  You have to run a program on your Ubuntu PC that periodically checks what your dynamic IP address is and passes that info on to the nameserver.

---

### Post by Madpilot on 2005-12-29
[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) will tell you how to set up a server, if your ISP allows.

---

