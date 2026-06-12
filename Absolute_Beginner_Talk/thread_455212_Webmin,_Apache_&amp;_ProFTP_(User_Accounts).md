---
title: "Webmin, Apache &amp; ProFTP (User Accounts?)"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-05-26
I'm trying to set up a basic development server.  I have a box on my network with fiesty installed.  I installed proftp, apache2, php, mysql.  I put webmin on it.

So, from my work box, I can ping, http, ftp to the hostname of the development box.

What I want is to do the following: I want [http://hostname/](http://hostname/) to load my home directory in apache.  I also want my ftp account to edit the same directory that is the [http://hostname/](http://hostname/) directory.

I then want to be able to create user accounts like "user2" that will map to [http://hostname/user2/](http://hostname/user2/) and create the ftp account "user2" so that [ftp://hostname/](ftp://hostname/) will be the same directory as the apache directory for user2.

I hope that makes sense.  I'm not sure if I need to do this all manually (if so, can anyone point me to instructions?) or if there is an easy way with webmin to do it all in one step.

Thanks!

---

