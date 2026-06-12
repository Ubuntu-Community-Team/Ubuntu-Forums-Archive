---
title: "Ubuntu 7.10 as server help"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2008-03-07
I have Ubuntu 7.10 set up pretty personalized. There for I'd rather not change it. But I want to set up a webserver for a domain now. Just something simple. Text, pictures, and video. No logins, billing, data bases. Is there any simple programs from Ubuntu I can use to serve basic .htm web pages? Web managment so one of my friends could edit the site would be nice as well. Any suggestions?

---

### Post by brettg on 2008-03-07
sudo apt-get install apache2

---

### Post by TekMuzik on 2008-03-07
> **brettg said:**
> sudo apt-get install apache2

Forgive me, I don't have much experience with web servers. I used a windows one named My First Webserver....so yeah. Isn't Apache pretty configuration intense? I have some Cisco training, but I'd like to keep it as simple as possible.

---

### Post by The Titan on 2008-03-07
apache isn't that bad... if you did that, you would probably have a perfectly good webserver. You should try it, you could always just remove it if you have problems

---

### Post by brettg on 2008-03-07
Not at all. Install apache and replace the default index.html with your own. voila, instant webserver!

---

### Post by TekMuzik on 2008-03-07
> **brettg said:**
> Not at all. Install apache and replace the default index.html with your own. voila, instant webserver!

Nice. Thanks. I'll give it a try.

---

### Post by hyper_ch on 2008-03-07
if it's just you who is going to use it you either need to

(1) chown/chmod the /var/www folder so that you can put stuff into it without being required to use root

or

(2) alter the base dir to your user's home somewhere

---

### Post by TekMuzik on 2008-03-07
Will modifying the permissions make it more vulnerable when exposed to the internets?  BTW...I love that quote about binary. :)

---

### Post by hyper_ch on 2008-03-07
> **TekMuzik said:**
> Will modifying the permissions make it more vulnerable when exposed to the internets?
It can - but not necessarily... 

as the default base dir /var/www is owned by root and neither you nor apache may write to it... so something has to be done... chmodding it to you won't have negative effects in that case.

---

