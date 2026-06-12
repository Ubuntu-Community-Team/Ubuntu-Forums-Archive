---
title: "Graphical port open/close representation?"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by YeahBuntu on 2006-09-20
Hello my good minded friends..

I am still a ubuntu noob but im working on it.

I hope someone can help me with this.. I am setting up my own webserver..

I should be at a point where I could create a virtual server within my router and forward the ports to see the good ol apache webserver "you did it!" page.

However I am not going that far with it yet.  Shouldnt I be able to put in the Internal IP address for the ubuntu/apache server on one of the other (in this case a windows computer on my LAN) and accomplish the same result? 
In other words Shouldnt I be able to put in xxx.xxx.xxx.xxx (of the ubuntu server into my web browser and see the apache screen?

So...If I should and I cant I am wondering if maybe its because all of the ports on my ubuntu system is closed... how can I tell .. is there a graphical representation where I can open and close ports somewhere?

Or am I totally offbase here... and you need more information from me.

Sorry to be a pain.

---

### Post by Jussi Kukkonen on 2006-09-20
Yes, you should be able to connect to apache using the internal IP. The first test is to try  [http://localhost](http://localhost) from the server itself (use w3m or other terminal browser if you don't have X running).

If you are not running a firewall on the server, the problem could be just a question of apache configuration (I don't remember Ubuntu defaults)... Check the config files in /etc/apache2/.

---

