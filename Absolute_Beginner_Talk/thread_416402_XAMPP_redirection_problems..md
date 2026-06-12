---
title: "XAMPP redirection problems."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by kerunt on 2007-04-21
Hi all,

Fresh newbie here :). I've played around with Ubuntu before, but nothing serious, 30 mins or so...

Today I got fed up with Windows and installed Ubuntu 7.04 on a fresh partition. I do a lot of php/mysql web development, so the first thing I did was look for a web-server. XAMPP came up pretty quickly in searches, so that's what I went with. It installed fine, but there's some annoying redirection thing that's driving me nuts. In the default DocumentRoot folder there is an index.html file which redirects all requests from [http://localhost/](http://localhost/) to [http://localhost/xampp/](http://localhost/xampp/). 

I changed the DocumentRoot and <Directory> paths in the Apache config file like I have done many times on Windows. I set both to /home/kerunt/!www. Now, I can access my files (which are located in my !www folder) fine, but the same redirection problem occurs. Accessing [http://localhost/](http://localhost/) redirects me to [http://localhost/xampp/](http://localhost/xampp/), which doesn't exist and results in a 404 error.

I've checked all config files and everything I could think of. I can't find any reference of that redirection.

However, I noticed that when I place an index.php in the root of the web-server, it loads and the redirection doesn't take place.

I just want the server to display the files and folders in my DocumentRoot, not redirect me somewhere. What should I do?

Thanks.

---

### Post by kerunt on 2007-04-21
Bump.

---

### Post by kerunt on 2007-04-22
Funny... problem has gone away by itself.

---

