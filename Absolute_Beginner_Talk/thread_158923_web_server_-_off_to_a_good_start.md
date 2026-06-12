---
title: "web server - off to a good start"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by tsharpe62 on 2006-04-11
Got my domain name. Signed up for DDNS and configured my router. Set up a starter web page. Intalled Apache2. I've searched and gone over the material that I could find here but some of it seems a little over my head at this point. I'm thinking at this point that I probably need to config Apache to connect my html page with my domain. Can anyone point to to a simple procedure for doing that or advise me of the next step. This isn't exactly easy but I'm having fun - kinda like golf. :D 

so far I've read
[http://help.ubuntu.com/starterguide/C/ch07s06.html#whatisapache](http://help.ubuntu.com/starterguide/C/ch07s06.html#whatisapache)
and
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

I'm sure I'll comprehend what I'm reading after the fact....:???:

---

### Post by jmartrican on 2006-04-11
After you did all that, what were you trying to accomplish that isn't working?

---

### Post by tsharpe62 on 2006-04-12
I'm thought that when I go to [http://sharpetek.com](http://sharpetek.com) that I should be seeing my start up web page pop up in my browser. I assumed after using synaptic package manager to install Apache that I would need to do some configuring - especially after reading over the material. Am I over complicating things?

---

### Post by jmartrican on 2006-04-12
[QUOTE=tsharpe62]I'm thought that when I go to [http://sharpetek.com](http://sharpetek.com) that I should be seeing my start up web page pop up in my browser. I assumed after using synaptic package manager to install Apache that I would need to do some configuring - especially after reading over the material. Am I over complicating things?[/QUOTE]

Did you try it first using straight up IP... [http://your_IP](http://your_IP) 
I resolved it to 68.178.232.100, is that your IP?  When I went to it it brought up the temp page from godaddy.  So it looks like the requests might not be making it to your server.  

How is your network setup?  Do you have a router doing NAT with a private netowkr behind it?  If so have tried connecting to your site on the private IP of your server?

---

### Post by Jimmey on 2006-04-12
Edit: I'm going to make this more detailed.

Your domain name is just a user friendly version of your IP. In my case, the domain's jimmey.ath.cx, and I am running two servers: an ftp ( [ftp://jimmey.ath.cx](ftp://jimmey.ath.cx) ), and http ( [http://jimmey.ath.cx](http://jimmey.ath.cx) ). If I where to be hosting a game server, people could connect using my domain name =-)

To make sure that your domain name is working, try > ping yourdomain in the command line, obviously replacing 'yourdomain' with your domain.

Apache works by publishing the HTML pages found in something called the DocumentRoot. You can define where this is by hand, but as a default, this is /var/www. This means that any pages put in /var/www are made available on the internet. 

This is only possible if Apache can listen on the default port: port 80. For it to be able to do this, you'll need to configure your router properly ( as I think you said you did. If you need further help with this, check [here]("http://www.portforward.com")), and you'll need to configure your computer's firewall properly.

Ubuntu's default firewall is called netfilter, and can be configured using the iptables command. But, it's not an enjoyable experience. Your best bet would be to download and install Firestarter, and allow all connections to port 80.

Hope this helps.

---

### Post by tsharpe62 on 2006-04-12
You were right jmartrican. I had to re-delegate my domain from go daddy to DynoDNS since I signed up for and activated DDNS in my router. Thanks!

Great info Jimmy! I'll move my html to /var/www this evening and I'll take your advice on using Firestarter instead of netfilter. I had seen Firestarter mentioned in my reading as a good pick. 

Thanks for the high quality assistance.

---

