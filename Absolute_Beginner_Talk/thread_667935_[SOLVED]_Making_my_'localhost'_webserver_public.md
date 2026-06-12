---
title: "[SOLVED] Making my 'localhost' webserver public?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-14
I'm a noob to Ubuntu, and I have recently setup a MediaWiki instance with Apache/MySQL/PHP; it works great. So much easier than doing it on Windows!

What I'd like to do is make it so I can access it from over the web; I have no idea how to do this.

I realize I will have issues since I don't have a fixed IP address; however it does stay static for quite a long time (I think) since I have a cable modem, and I don't mind having to enter in a new IP address whenever it changes.

I don't want the wiki open for public consumption (at least not yet), but rather just as an updateable reference throughout the day.

Any advice/links/book references for achieving this webserver functionality (with a nominal amount of security) are most appreciated!

---

### Post by benanzo on 2008-01-14
If you want to run a personal site off your home internet connection I would recommend you use something other than port 80 otherwise you'll get loads of crawlers and bots looking at your stuff.  Have a look at robots.txt and .htaccess if you want to setup some security, ie restricting access to users with passwords and preventing google/yahoo bots from indexing your site, otherwise you'll show up in search results...which you don't really want since your bandwidth will get crushed.

---

### Post by teryowen on 2008-01-14
i assume your behind a router what you want to do is forward the port in use to your current computer where the server is at so say the server is 192.168.1.103

forward port 80 or wvr u use to 192.168.1.103
you could use other ports but then in the address bar you would have to put
123.45.67.89:55
where the first part is ur ip and the 2nd is the port.

look here to set up a link to your ip
[https://www.dyndns.com/](https://www.dyndns.com/)

---

### Post by ajopaul on 2008-01-14
if you are using a DSL router then open up your router settings from browser [http://192.168.1.1](http://192.168.1.1) assuming router ip is 192.168.1.1 the username password is usually admin admin then modify your virtual server settings to open up local ports..

---

### Post by hyper_ch on 2008-01-15
So, you're behind a router..... then

(1) give your server a static IP in the lan.

(2) forward port 80 from the dsl modem/router to your server

(3) signup for a dynamic ip service such as [www.no-ip.com](www.no-ip.com) or [www.dyndns.com](www.dyndns.com)

(4) install the updater programs accordingly. Both, no-ip and dyndns have their program in the repositories. They will then set your ip correctly every hour or so.

(5) you can access your machine from an domain like:   myserver.no-ip.com  or myserver.dyndns.com

---

### Post by jjsonp on 2008-01-15
Thanks for the great tips; I will be trying this probably tonight.

---

