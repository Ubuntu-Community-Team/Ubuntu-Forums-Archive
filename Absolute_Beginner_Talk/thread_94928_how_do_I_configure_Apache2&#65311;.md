---
title: "how do I configure Apache2&#65311;"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by 0okami on 2005-11-25
i remember in windows there were a few txt files to write to and change.... 
But I dont see anything similar in linux...

Im wanting to setup custom 404 and learn how to set other options, but the manual is too advanced for me still. 

Any idea how to do basic apache configurations?

---

### Post by odin on 2005-11-25
the files you are looking for are in /etc/apache2(httpd.conf,apache2.conf) but if you are not a bit more specific in what you need I cant help.For the thing you said about the 404 you should look in apache2.conf.

Everytime you modify something in the apache configuration remember to restart the server with:

/etc/init.d/apache2 restart

Hope this helped you a bit.

---

### Post by 0okami on 2005-11-27
[QUOTE=odin]the files you are looking for are in /etc/apache2(httpd.conf,apache2.conf) but if you are not a bit more specific in what you need I cant help.For the thing you said about the 404 you should look in apache2.conf.

Everytime you modify something in the apache configuration remember to restart the server with:

/etc/init.d/apache2 restart

Hope this helped you a bit.[/QUOTE]

Thanks! this was big help! I really appreciate it. :)
[http://65.189.185.5/thisisarandomlink](http://65.189.185.5/thisisarandomlink)
^ shows custom 404 working ok. :) (untill my ISP switches my ip address)

---

### Post by 0okami on 2005-11-27
[QUOTE=odin]but if you are not a bit more specific in what you need I cant help.[/QUOTE]

glad to se you dont mind :) I had another question, after initial install, is apache2 ready to put to the world?&#12288;Or, are there some settings you would recomend tightening?

---

### Post by odin on 2005-11-28
Well that depends again on your needs.But if you are talking about security,for example,I can tell you I never had any problems with it...but that doesnt mean I could have had them...

If you just need to put a web into the real world there are just a couple of option(domain name for example) you have to change but the rest should work.Of course you can customize it but work,it will work.

---

