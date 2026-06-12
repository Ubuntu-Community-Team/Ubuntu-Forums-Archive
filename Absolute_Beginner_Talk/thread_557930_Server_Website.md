---
title: "Server Website"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by mattc908 on 2007-09-23
Okay so this is whats going on. I have Ubuntu Fiesty server.... LAMP, with PHP5 installed, an FTP, and some other stuff. I have it on a DYNDNS. I have a folder with a website in it. How would I link that so that when they go to mattc908.dyndns.org that is what it would show? If you go to mattc908.dyndns.org it just shows that apache works. Thanks!

---

### Post by DBStevens on 2007-09-23
I suspect if you were to put a file named index.html in the directory tree one level above the   apache2-default directory your site is providing when accessed by [http://mattc908.dyndns.org/](http://mattc908.dyndns.org/)  it might show your page.

It however is possible that the server version of Fiesty (like the other versions)  is also doing a redirect match so the above action might not have any effect.

If that is the case you'll need to change the default configuration to remove the redirect match container.

---

### Post by mattc908 on 2007-09-23
How would I edit apache default directory like whats that file called, sudo nano /?/?/?
Im completly new to this.

---

### Post by mattc908 on 2007-09-23
Nevermind figured it out:
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

### Post by DBStevens on 2007-09-23
Glad to see you found what you needed.   I spent most of today offline getting the house ready for winter.

I got a chuckle out of the default Ubuntu Apache setup, but there is a reason that Ubuntu does some things a bit different.

There are many ways of getting the deed done.

---

