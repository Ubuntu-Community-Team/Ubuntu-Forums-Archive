---
title: "Unable to open xxx.blogspot.com"
date: 2010-02-02
forum: Bangalore Team
---

### Post by richlyn9 on 2010-02-02
This is a unusual situation that i am in.
[http://(anything).blogspot.com/](http://(anything).blogspot.com/) wont open in firefox
error: sever not found

i am on a aircel gprs connection using my phone as modem and in 9.10
i tried opening the site on the phone browser and it did not open, error: site not found.

---

### Post by SoFl W on 2010-02-02
I tried some blogspot sites that I visit and they worked.  Did you try 
[http://blogspot.com](http://blogspot.com)
or
[http://www.blogger.com/](http://www.blogger.com/)

---

### Post by richlyn9 on 2010-02-02
yeah [www.blogger.com](www.blogger.com) and dashboard  opens but nothing else.Cannot open to see posts

---

### Post by richlyn9 on 2010-02-03
i pinged [www.rxezlqu.blogspot.com](www.rxezlqu.blogspot.com)  but it could not  and i tried pinging its IP which did ping
however its not just a particular blog that dosent op up but any blog


i also checked for open ports 
richlyn@richlyn-lucid:~$ netstat -anp --tcp --udp | grep LISTEN
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN   

any ideas what the matter might be?

---

### Post by jrusso2 on 2010-02-03
I logged into my blog on blogspot and it worked fine.

---

### Post by richlyn9 on 2010-02-05
so it seems i have a issue with my isp or a dns issue

---

