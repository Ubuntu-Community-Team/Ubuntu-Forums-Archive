---
title: "Desktop Server"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-17
I am trying to get a message board set up on my ubuntu desktop machine.
[COLOR="Red"]Very few users[/COLOR]

I installed apache2 a week or so ago and my sister on the otherside of the earth could access my machine and saw the "powered by apache" logo.  I was excited. (I had to open port 80 to my machine through my linksys)

Now I found phorum.  Seems nice.  I want to install it.  I downloaded it and unpacked it in /var/www/board.

I installed php4 and mysql(wanted mysql anyways for other stuff).
I followed a tutorial on here on how to install "LAMP".

Now I can't access my machine from my ip.

Did I do something wrong? How do I make sure everything is set right so I can rule out "me" as the cause for the world not seeing my website. 

[COLOR="DarkOrange"]http://localhost/<anything>[/COLOR] works.
[COLOR="DarkOrange"]http://192.168.1.120/<anything>[/COLOR] says connection refused.
[COLOR="DarkOrange"]http://<myip>/<anything>[/COLOR] times out.

Thanks for your expert opinions.

---

### Post by Jimmey on 2006-05-17
Try installing firestarter and opening port 80 on your machine, as well as on your router.

**Edit:** Is your IP static? Make sure it is.

---

### Post by morequarky on 2006-05-17
My isp changed today.  That probably had something to do with it.  It works now.  The new ISP has given us a static IP.  The last company gave us a static IP too I think, but didn't promise it would stay.  This ISP said it is truly static.

I still need some help getting the message board working.  I will look around for some help on phorum.

Another question...How do I get Domain names pointed at my server?  Where can I get a DNS server to point my domain names at my ubuntu box.  Again, very little real traffic is expected.

thanks.

---

### Post by skippy81 on 2006-05-17
To set up something like forum software you just copy it into a public directory on your webserver and navigate to it with a browser.   Just follow the instructions it gives you, especially any about deleted folders.  

As for DNS, normally the company who you registered your domain with will supply a free dns service.  You just type in your IP (use dyndns.org) to find your IP and submit it to the company. 

You need to not only open a port on your router but also port forward port 80 to your linux box.  You will also need to go into your apache config file and tell apache your domain name, this is especially important if you are hosting multiple domains on the same server.

---

### Post by morequarky on 2006-05-17
[COLOR="DarkRed"]> also port forward port 80 to your linux box. You will also need to go into your apache config file and tell apache your domain name, this is especially important if you are hosting multiple domains on the same server.[/COLOR]
Wow,  I don't know how to do that.

Currently, when I navigate to my web folder with firefox, the website I want is returned properly using my ip address.  [COLOR="RoyalBlue"]How do I tell apache my domain name?[/COLOR]

I am working with tech support on the DNS thing.  They have the command hidden in some far away corner of their GUI and the directions they gave me don't work, yet.

I think I have locked myself out of my mysql account. [COLOR="Red"] D'Oh.[/COLOR]  How do I get access?  Reinstall it?  Delete a file?  ](*,)

There is a few files I have to configure before I can navigate to the forum and have it just "work".  It has to be connected to mysql first and sure enough, I don't know how to get into mysql.  I messed it up.

---

### Post by Jimmey on 2006-05-18
For a domian name, try [www.dyndns.org](www.dyndns.org).

To tell apache your domain name, and to make it work with the www. prefix, you'll need to set up a virtual host block in your httpd.conf.

To edit the httpd.conf, you'll first need to make a backup:
[/quote]sudo cp /etc/apache2/httpd.conf /etc/apache2/httpd.conf.bak[/quote]

Then you can use gedit to insert the virtual host block: 
> gksudo gedit /etc/apache2/httpd.conf

The virtual host block should look something like this:

> <VirtualHost = domianNameHere>
serverName = [www.current](www.current) domain name
</VirtualHost>

Replacing the "domainNameHere" with your raw domain name, like jimmey.ath.cx;
And replacing the "www.current domain name" with your domain name, with a www. prefix, like [www.jimmey.ath.cx](www.jimmey.ath.cx).

---

### Post by morequarky on 2006-05-18
> **Jimmey]For a domian name, try [www.dyndns.org](www.dyndns.org).

To tell apache your domain name, and to make it work with the www. prefix, you'll need to set up a virtual host block in your httpd.conf.

To edit the httpd.conf, you'll first need to make a backup:
> sudo cp /etc/apache2/httpd.conf /etc/apache2/httpd.conf.bak

Then you can use gedit to insert the virtual host block: 


The virtual host block should look something like this:



Replacing the "domainNameHere" with your raw domain name, like jimmey.ath.cx said:**
> www.jimmey.ath.cx[/url].

Ah great thanks. I'll try that.

I got the message board up and running with the domain name pointing at it this afternoon after fixing numerous annoying things, but non of them were major.

Question.  I have two domains available to me.  Can I point them at different folders?  How would I do that?

---

### Post by morequarky on 2006-05-18
Ok.  I tried your code and it didn't work.

I went to apache's website and found all kinds of wonderful documentation for each version of apache.  I looked at version 2.0 and 2.2.  Both had fantastic docs.  Only thing is...NONE of the syntax in the docs worked!

What am I doing wrong?

---

