---
title: "[SOLVED] PHPMyAdmin Problems"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-12-01
I've got my LAMP installed, apache is running and so is MySQL.  Learning what little I do know about MySQL databases through PHPMyAdmin, I installed PHPMyAdmin because frankly the command line would take me a while to achieve my development tasks.

Anyway, I can travel to [http://localhost](http://localhost) and it displays the directory for /var/www/  but if I travel to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  , it did nothing.  So I symbolically linked the /var/www/ folder with /etc/phpmyadmin/ and now if I travel to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) it displays the directory of course of /etc/phpmyadmin.

What I want to happen is when I go to localhost/phpmyadmin is that it fires up the interface in my browser for PHPMyAdmin.  I'm not sure where to symlink this at or where that index file is even located at on my machine.

---

### Post by mdbarton on 2007-12-02
I have exactly the same problem.  [http://localhost/phpmyadmin](http://localhost/phpmyadmin) returns a blank page.

I tried:
> cd /var/www
sudo ln -s /usr/share/phpmyadmin phpmyadmin
and now get a phpmyadmin link in [http://localhost](http://localhost) but still a blank page on [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

If I go to [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) the browser tries to download the php file, so it seems that the apache setup for phpmyadmin is not correct.  I have info.php on [http://localhost](http://localhost) and this works fine, and if I rename this to index.php it is loaded as the index page.

---

### Post by siciliancasanova on 2007-12-02
Ok so I reinstalled my base set up last night to have a fresh install to do this [http://www.youtube.com/watch?v=60_nU9XZOIQ]("http://www.youtube.com/watch?v=60_nU9XZOIQ")

and figured it would be a good opportunity to reinstall LAMP.  Well I have done so and still everything is running, MySQL, Apache2, PHP5... i've got MySQL Admin running at the moment it's able to connect to localhost with the username fine and what have you.

If no one has an idea on this problem, I've seen about 4 or 5 others with unanswered posts with essentially the same question, does anyone have any tips/links for PHP forums or IRC chat that might be able to help?

Edit:  I suppose I should mention that the problem is still there, [http://localhost/phpmyadmin](http://localhost/phpmyadmin) is brining up null (404)

---

### Post by annda on 2007-12-02
being a local directory, this is case sensitive, so you need this URL
[http://localhost/phpMyAdmin/](http://localhost/phpMyAdmin/)

---

### Post by siciliancasanova on 2007-12-02
Still nothing man

---

### Post by ruibernardo on 2007-12-02
mdbarton, do not link the phpmyadmin directory to /var/www. Remove the link if you did it. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=591952") to know why and how to only allow access to phpmyadmin to some pre-defined IP.

About the other problems I'm not sure what it is but do you have cookies enabled and/or allowing localhost to create cookies? Do you have javascript enabled on Firefox? Are you using noScript?

---

### Post by siciliancasanova on 2007-12-02
Thank you, that thread got it working for me.

Last night I figured it was a symlink issue and did my own symlink but it was the the wrong link.  Thanks for posting that.

---

### Post by annda on 2007-12-02
do you still get the 404 error? if so, check the symlink. 

```
ls -l /var/www
```

make sure the target is right. i did a manual install so my phpA is in apaches dir, but i just  put it into /etc symlinked and it stil works fine.

UPDATE: too late again...

---

### Post by ruibernardo on 2007-12-02
Glad it worked :)

---

