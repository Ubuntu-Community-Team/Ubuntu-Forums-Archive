---
title: "Server Set Up"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Tux.Ice on 2008-01-14
Hi,

i was wondering if i can set up a website server (to host my website) on my laptop running ubuntu gutsy desktop. i have a domain its techotec.com and there is currently my website rough on it :) if anybody could help that would be appreciated

thanks

---

### Post by Pevichaey5 on 2008-01-14
you'll need a static ip address (one that never changes), plenty of bandwidth, and stuff

i'm just hosting a website/forum for my house, you will also have to register the domain name, which i'm not sure how

---

### Post by Tux.Ice on 2008-01-14
ive got a static ip, super bandwidth, and the domain is already reg'd

---

### Post by Pevichaey5 on 2008-01-14
ok

assuming your on a shared network, you need to set port forwarding requests to your computer/server

then install apache2 and all the necessary modules like php, mySQL etc

then the website files will be here

/var/www

i also downloaded a virus scanner, as my server is also hosting files around my network which is good because all the clients are windows lol

if your going to put mysql on, i'd suggest also installing phpmyadmin then visiting this link

[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

then you can set up your database, and things

---

### Post by Tux.Ice on 2008-01-15
thanks ill do it right now

---

### Post by hyper_ch on 2008-01-15
static IP is not required (but very, very much recommended if you also want to operate an email server.
For setting up a full-fledged ISP-like hosting configuration have a look at the perfect server howtos over at [http://www.howtoforge.com](http://www.howtoforge.com) . However if you just want to setup a "testing" environment without different users having ability to create and maintain websites and without email server and stuff... then you can do that fairly simple by just installing apache2, php5, mysql

---

### Post by SniperClops on 2008-01-15
nm

---

