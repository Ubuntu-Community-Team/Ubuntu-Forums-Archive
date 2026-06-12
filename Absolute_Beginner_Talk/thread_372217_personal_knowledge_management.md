---
title: "personal knowledge management"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2007-02-27
Hello. After some search I found that mediawiki software is best for knowledge management. But it needs server. Is there any desktop server that is used to install mediawiki onto  for my Ubuntu computer ? If so how can I do that?
Thanks in advance.

---

### Post by rjfioravanti on 2007-02-27
When you download a mediawiki package, it is just a bunch of html files and php files that you can set up if you have a web server set up

When I setup a wiki, I used apache2, and php5, and then I created a symbolic link in /var/www/ directory to the location of my mediawiki directory. Then when you connect to localhost/wiki/ or whatever you call the link, it will load the wiki in your browser

You also need mysql or something set up

---

### Post by xunshirine on 2007-02-27
> **rjfioravanti said:**
> When you download a mediawiki package, it is just a bunch of html files and php files that you can set up if you have a web server set up

When I setup a wiki, I used apache2, and php5, and then I created a symbolic link in /var/www/ directory to the location of my mediawiki directory. Then when you connect to localhost/wiki/ or whatever you call the link, it will load the wiki in your browser

You also need mysql or something set up
Thanks @rjfioravanti . But could you say to me what is localhost? I highly intend to save my  data on my computer not on web. Does localhost provides me that?

---

### Post by rjfioravanti on 2007-02-27
localhost is your computer (127.0.0.1)

If you are not wanting to put this on the web, I am not sure you want to use mediawiki, generally wiki's are for collaboration between a group of a people, usually more than a few. If you are just doing this for yourself it may be overkill.

So what I was saying is...
if you install apache2 you are making a web server

If you have a web server like apache running, and you type localhost into your browser, it should look to you /var/www/ directory for a file called index.html, and it will display that in your browser

say you put your mediawiki package, in a directory called wiki, that you put in /var/www/
then if you type localhost/wiki/ into your browser, it should look to /var/www/wiki/ on your machine for index.html, which is provided in the mediawiki package

---

### Post by xunshirine on 2007-02-27
> **rjfioravanti said:**
> localhost is your computer (127.0.0.1)

If you are not wanting to put this on the web, I am not sure you want to use mediawiki, generally wiki's are for collaboration between a group of a people, usually more than a few. If you are just doing this for yourself it may be overkill.

So what I was saying is...
if you install apache2 you are making a web server

If you have a web server like apache running, and you type localhost into your browser, it should look to you /var/www/ directory for a file called index.html, and it will display that in your browser

say you put your mediawiki package, in a directory called wiki, that you put in /var/www/
then if you type localhost/wiki/ into your browser, it should look to /var/www/wiki/ on your machine for index.html, which is provided in the mediawiki package
Thank you so much. I know mediawiki is for collaboration but personal knowledge management softwares are not as handy as mediawiki is. It is hard to work with but I can manage. Thanks again.

---

### Post by 23meg on 2007-02-27
Check out Instiki as well, which is simpler and pretty much standalone. Recent versions require a MySQL backend.

---

