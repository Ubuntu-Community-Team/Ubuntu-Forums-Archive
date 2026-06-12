---
title: "How to host a website?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-04-15
How would I host a website on Ubuntu?
I have Apache Webserver, a firewall installed on the computer, with only port 80 open, port 80 fowarded on the router, my IP is pretty much static (technically dynamic, but it's been the same for around 1 year). I have an old computer, with an ethernet cable ran to it, with Kubuntu installed. Where do I go from there?

---

### Post by Seisen on 2007-04-15
Check out this website and see if it helps.

[http://www.dslwebserver.com/]("http://www.dslwebserver.com/")

---

### Post by nhandler on 2007-04-15
By default, you put your html files in /var/www. Now, you can test your server by entering localhost (127.0.0.1) in the address bar of your browser. If all goes well, you should see /var/www/index.html displayed. To get to your site from another computer, enter your computer's ip address as the url. You can use a service like noip to get something like yoursite.something.com so you don't need to memorize your ip.

---

### Post by Peter1234123 on 2007-04-15
If I were to buy a domain name, I would just make a redirect domain to (myip):80? And how would I setup PoP3 email boxes?

---

### Post by nhandler on 2007-04-15
Pop3 is totally different than apache. I believe postfix is the application that you will need.

---

### Post by Peter1234123 on 2007-04-15
Then how would I make email boxes such as Administrator@(mydomainname)? I think I need a DNS server, correct?

---

