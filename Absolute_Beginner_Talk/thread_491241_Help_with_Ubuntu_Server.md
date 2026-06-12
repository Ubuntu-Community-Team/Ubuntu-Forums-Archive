---
title: "Help with Ubuntu Server"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by RaidenPryde on 2007-07-03
Ok basically, My partner and I just installed Ubuntu 7.04 server ed. 
We run a LANcenter and we're using Ubuntu for a web server.
we have Ubuntu, Lamp, and Gnome installed.
and quite frankly.. we have NO idea what we're doing.
so if anyone knows how to set up a web server with what we have. HELP
Much Appreciated.

HEEEEEEELLLLLLLP
Ok, My partner and I just installed Ubuntu, LAMP, and GNOME.
We're planing on using the computer for a web server. 
so heres my question(s).
HOW do we do it
WHAT else do we need to install?
if anyone knows, your assistance would be much appreciated.

---

### Post by Ek0nomik on 2007-07-03
What are you trying to do?

You have Ubuntu, which is the L in "LAMP" installed you say?  You have Apache, MySQL, and PHP?

I believe the Apache root folder is in /var/www/

You will want to put your html pages in there.

---

### Post by Rocket2DMn on 2007-07-03
If you are running this server behind a router, you will have to configure port forwarding or even DMZ on the router.  In this case, using a static internal IP is suggested so you don't have to change the port adjustments if the internal IP changes.
There are many websites out there to help you configure Apache, the web server program.  The directory can vary depending on which httpd (the apache daemon) you have active.  Run a google search for something like "apache configuration" or "apache setup".  It should probably be running by default on the server edition.
```
locate apache
or
whereis httpd
```
can help you find which directories apache is available in.

---

### Post by LaRoza on 2007-07-03
How did you install? Did you install the server version?

---

### Post by dexter on 2007-07-03
I believe that everything is already configured if you installed lamp and you're ready to go. Try opening a browser and go to "localhost". Do you see an apache webpage coming up ? If so, you're ready to go. The standard webpages are found in /var/www.

---

### Post by az on 2007-07-03
> **RaidenPryde said:**
> Ok basically, My partner and I just installed Ubuntu 7.04 server ed. 
We run a LANcenter and we're using Ubuntu for a web server.
we have Ubuntu, Lamp, and Gnome installed.
and quite frankly.. we have NO idea what we're doing.
so if anyone knows how to set up a web server with what we have. HELP
Much Appreciated.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by akshaysrinivasan on 2007-07-03
Well , I think you'd have started using Apache.Just create your machine , toughen the security , create your web page , and that's about it.I think you better get a book on LAMP.By the way , if you have a router and home Internet connection , you'll probably need to setup port forwarding too.

---

### Post by bodhi.zazen on 2007-07-03
Please do not double post. It leads to duplication of effort from those trying to help and confusion when trying to follow up with what has been advised/done.

You can also try this : [http://doc.gwos.org/index.php/HowToServerGuide](http://doc.gwos.org/index.php/HowToServerGuide)

Last, "Server" is a very broad term as you can see; please try to be as sepcific as possible. Help with FTP, apache, samba, security, etc ...

---

### Post by bodhi.zazen on 2007-07-03
Threads merged (3 total)

---

