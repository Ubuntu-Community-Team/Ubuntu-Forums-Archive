---
title: "Webserver in Ubuntu"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by AtinLango on 2006-03-21
I have never hosted a webserver or mail server (except for something called mdaemon in Windows). Now that I have Ubuntu, I want to know the following:

1.If I have a webserver software like Apache, and a good hardware server with Ubuntu and broadband, is there anything else I need to be able to host my website?
2.Can Apache also serve mail? If not, is there a good open source program I can use for serving mail?
3.What software would I need to host a forum like this one using Ubuntu server? Any additional requirements?

---

### Post by bjweeks on 2006-03-21
> 1.If I have a webserver software like Apache, and a good hardware server with Ubuntu and broadband, is there anything else I need to be able to host my website?

If you have a static ip you need a domain name or if you have dynamic ip get a [http://dyndns.com](http://dyndns.com) name.

> 2.Can Apache also serve mail? If not, is there a good open source program I can use for serving mail?

No. Yes, many.

> 3.What software would I need to host a forum like this one using Ubuntu server? Any additional requirements?

Php and forums software of your choice(ubuntu forums uses vBulletin and it is not free).

---

### Post by mority on 2006-03-21
[QUOTE=AtinLango]1.If I have a webserver software like Apache, and a good hardware server with Ubuntu and broadband, is there anything else I need to be able to host my website?
2.Can Apache also serve mail? If not, is there a good open source program I can use for serving mail?
3.What software would I need to host a forum like this one using Ubuntu server? Any additional requirements?[/QUOTE]

1. No, you need nothing else. But there are a few things you should consider:

As a private home user, you normally don't get a fix IP address from your ISP so the public IP address of your server will change every 24 hours or so. As a workaround there is a service called [DynDNS](http://www.dyndns.org). But you will have to configure your router to work with DynDNS or install a DynDNS client on the server if it is connected directly to the internet.

The other thing is that the bordband internet connections for home users are usually asynchronous. That means, you have between 1 and about 15 mbit/sec download bandwith, but only a fraction of it upload bandwith (maybe between 128 and 768 kbit/sec) But the upload bandwith is the important factor when someone in the internet wants to get data from your server. That is not a big problem as long as the number of server accesses from the internet keeps low. But you should know that you can't host a frequently accessed server with hundreds of requests per hour with an ordinary home user broadband internet connection.

2. Apache is a webserver, not a email server, so: no. There are plenty of servers for Linux. I think exim and postfix are the most famous.

3. The most popular open source forums software is [phpBB](http://www.phpbb.com). It is not as feature rich as this Ubuntu boards, but it's quite good. See it in action as a [Debian Board](http://forums.debian.net) and as a [Gentoo Board](http://forums.gentoo.org).
You need PHP support for your Apache to run the board. Install the package 'libapache2-mod-php5' if you installed apache2.

---

### Post by AtinLango on 2006-03-21
Thanx guys, thats great. Let me find time and follow the links you have given. Then i get back.

EDIT: But i think I would also need a DBMS, like mysql for the forum. And for webserver, I dont necessarily, unless I want it database enabled.

And yeah, I have checked the debian forum. It isnt as good as this one.

---

### Post by mority on 2006-03-21
[QUOTE=AtinLango]EDIT: But i think I would also need a DBMS, like mysql for the forum. And for webserver, I dont necessarily, unless I want it database enabled.[/QUOTE]

Yes, you're right. You need a database system to run phpBB. I forgot about it. Just install package 'php5-mysql'. The dependencies should do the rest. And I would recommend to install phpMyAdmin too for easier maintenance of the database system (unless you're a SQL guru ;)).

I know that the board software used by this forum (vBulletin) is more powerful than the current stable version of phpBB, but vBulletin is not free. And if you are not planning to set up a board with thousands of regular members, phpBB will do the job more than good.

---

### Post by rklauco on 2006-03-21
Check this URL:
[http://www.howtoforge.com/perfect_setup_ubuntu_5.04]("http://www.howtoforge.com/perfect_setup_ubuntu_5.04")
Nice how-to, works for 5.10 too.

---

