---
title: "[SOLVED] httpd (no pid file) not running"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2007-10-27
So, I'm running a local installation of Apache with PHP, Rails, Python, etc. It has been running perfectly for several months. Today, I went to install a new Virtual Host, and had a brain fart and thought I was supposed to edit httpd.conf.

I ran sudo gedit /etc/apache2/httpd.conf, and noticed that the file was blank. So, I went and edited sites-available/default like normal. The only problem is, now when I try to restart apache, I get the following message:

 * Forcing reload of web server (apache2)... 
httpd (no pid file) not running

I removed the new virtual host, and this still happens. Is there anything I can do to restore whatever I've broken, or am I going to have to reinstall everything to do with Apache? If I have to reinstall, is there any way I can keep my various modules?

Thanks for any help.

---

### Post by Zamber on 2007-12-16
Why is this posted as SOLVED?

---

### Post by flamingsole on 2007-12-16
It fixed itself when I restarted my computer. It was really weird.

---

### Post by webwolf_3000 on 2008-02-12
Just a thought, but when you do resolve something - might be cool to let people know how it got resolved. help all the other n00bs out :)

---

