---
title: "Developing with Ruby on Apache"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-12-01
I have Ruby on Rails installed and can create an application of course with <code>rails test</code> it creates the framework for the ap.  

That's all fine, now my shared host runs apache so despite the problems Ruby has with apache I need to run it on Apache.  So I have Apache2 installed and <code>http://localhost</code> brings up the apache directory.

I have never developed completely in Linux before and am quite new to Ruby.  Where I'm stuck at and where I need a little help is how can I get into phpMyAdmin and create new databases and how can I configure Apache to work with Ruby and work out of my folder that has/will have all my projects in, so say /home/development/someprojectfolder/index.rhtml

Most of the guides have all worked for me, as far as installing goes but I haven't really found much help beyond that of just getting to hello world on apache.

---

### Post by siciliancasanova on 2007-12-01
Ok I just installed PhpMyAdmin which uninstalled PHP and Apache2 and reinstalled it, 

[http://localhost](http://localhost) is still showing the apache directory but now
[http://localhost/phpmyadmin](http://localhost/phpmyadmin) is bringing up a 404 error

EDIT:

Ok following this [https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29#head-2b91cc1ce37842102d20e88e029477b035bee150]("https://help.ubuntu.com/community/ApacheMySQLPHP?highlight=%28apache%29#head-2b91cc1ce37842102d20e88e029477b035bee150")

I've done everything, and the phpmyadmin portion seems to be the least descriptive that just says to install it and that's it.  Now I believe the solution to my previous issue of the directory being home/development , i should just have to link that to var/www correct?

---

