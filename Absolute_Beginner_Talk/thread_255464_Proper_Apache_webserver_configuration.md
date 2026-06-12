---
title: "Proper Apache webserver configuration?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Average Joe on 2006-09-11
Hi,

I have installed Apache2 and PHP succesfully on my Ubuntu 6.06 box. I just want to use it for development purposes, so the websites I make should not be visible to the outside world. Although everything works fine, I am not sure whether I have configured it correctly when it comes to security and proper configuration.

I just want to learn a bit more about how Apache should be set up correctly for home development, so if anybody could comment on my current configuration, I would appreciate it a lot.

Here it goes. I noticed that, after installing Apache, there were two entries in my /etc/hosts file (apart from the ip6 stuff):

127.0.0.1 localhost
127.0.1.1 ubuntu

(ubuntu is the name of my box.) So if I type [http://localhost/](http://localhost/) or [http://ubuntu/](http://ubuntu/) in the address bar of my browser, I get the default Apache page locally stored at /var/www/.

For development purposes, I find it convenient to store my websites in my home directory. Therefore, I first created two new directories:
/home/joe/www/
/home/joe/cgi-bin/
Then I went to the /etc/apache2/sites-available/ directory and copied the file default to ubuntu. In the new ubuntu file I changed the first two lines to:
 
NameVirtualHost 127.0.1.1:80
<VirtualHost 127.0.1.1:80>

and I set the DocumentRoot to /home/joe/www/ and the cgi-bin to /home/joe/cgi-bin/.

Next, I made a symbolic link /etc/apache2/sites-enabled/ubuntu linking to /etc/apache/sites-available/ubuntu. After restarting the apache server (apache2ctl -k restart), I now get the default Apache page when I go to [http://localhost/](http://localhost/) and I get my own stuff when I go to [http://ubuntu/](http://ubuntu/).

However, when restarting the Apache server, I got a message saying that the server's full qualified domain name could not be determined. To "solve" this, I put a line:

ServerName localhost:80

in the /etc/apache/apache2.conf file. Then the message does not appear any more.

Furthermore, for security reasons, I changed content of the /etc/apache2/ports.conf file to:

Listen 127.0.0.1:80
Listen 127.0.1.1:80

This should (I think) make sure that the server only listens to port 80 of my local ip addresses.

And that's it. Can anybody tell me if this is the proper way of doing things, and whether it is secure? I am not behind a router, and I don't use a firewall.

Thank you for reading this. Any comments are most welcome.

---

### Post by Klaidas on 2006-09-11
Hmm.
Well, I myself just blocked port 80, which apache uses by default, to be accessed from the outside :) But I don't think this is the proper way, specially when you're studying apache's configuration.

I'd be interested in this question too.

---

### Post by Average Joe on 2006-09-11
> **Klaidas said:**
> Hmm.
Well, I myself just blocked port 80, which apache uses by default, to be accessed from the outside :) But I don't think this is the proper way, specially when you're studying apache's configuration.

I'd be interested in this question too.

I thought that, from a security point of view, it doesn't really matter what port you are using. But I am not an expert, that's why I started this thread in the first place :).

---

### Post by indytim on 2006-09-11
I think this link may help you.  Note the section on securing Apache.

[https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28Apache%29]("https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28Apache%29")

Regards,

IndyTim

---

### Post by Average Joe on 2006-09-11
Thanks IndyTim, I didn't know that I could find more information about it even on the Ubuntu website. I will check it out immediately.

---

### Post by Average Joe on 2006-09-11
Ok, I went through it. Apart from the Listen ports, which I apparently configured correctly, there is not so much additional information in there. (I don't run a MySQL server, I have got my hands full on writing correct HTML and PHP already.)

I digged a bit more into the group and user policy of the Apache server. For my configuration, the user and group is www-data. I saw that the default shell for this user is /bin/sh and I changed it into /bin/false to make sure that no shell scripts can be executed by this user. (I am not planning on using any CGI scripts either, at least not for now.)

---

### Post by clarkth on 2006-09-11
Joe,

Thanks for posting this info, I'm about to start a development box also and was wondering how to do exactly what you've done.

---

### Post by Average Joe on 2006-09-12
I am glad my post could help you a little. Good luck setting up your development box. Please let me know if find out more about any configuration/security issues. I am still hoping some "expert" can give me some feedback on this.

---

