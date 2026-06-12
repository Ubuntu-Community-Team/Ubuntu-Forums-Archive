---
title: "[SOLVED] Php"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by anderskitson on 2008-03-18
I am trying to set php, Apache is working, but when I try and go to the test link for php [http://localhost/testphp.php](http://localhost/testphp.php) It trys and downloads the file, not view it in the browser.

This is whats in code in the file > <?php phpinfo(); ?>
And is located in /var/www/testphp.php 

I have tried restarting apache, and it says it succesfuly does so, but still the same problem.
 
Someone had told me to type this > grep -R php /etc/apache2/*
and I got this output
> /etc/apache2/mods-available/dir.conf: DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
/etc/apache2/mods-available/php5.conf:<IfModule mod_php5.c>
/etc/apache2/mods-available/php5.conf: AddType application/x-httpd-php .php .phtml .php3
/etc/apache2/mods-available/php5.conf: AddType application/x-httpd-php-source .phps
/etc/apache2/mods-available/php5.load:LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
/etc/apache2/mods-enabled/dir.conf: DirectoryIndex index.html index.cgi index.pl index.php index.xhtml

The only other thing I could see as a problem my self was that my httpd.conf file only had this text in it

> servername localhost

Any help would be greatly appreciated

---

### Post by Xiong Chiamiov on 2008-03-18
How did you install Apache/PHP?

---

### Post by anderskitson on 2008-03-18
[http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies) I was Following this site tutorial, Im running Gusty Gibbon so maybe that's the problem

---

### Post by Xiong Chiamiov on 2008-03-18
That looks fairly similar to [how I installed it]("https://help.ubuntu.com/community/ApacheMySQLPHP").  You can also give [XAMPP]("http://ubuntuforums.org/showthread.php?t=223410&highlight=xampp") a try if you wish, though I had some weird problems with MySQL that appeared.

The only thing I'm thinking of (since .php is automatically interpreted by the php interpreter) is that there might be something odd about newlines.  Then again, that doesn't make any sense, but it's caused me much headache before.

Aha, I should actually look at what I [link you]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-59bdeb1f6438eddbde544b41ca0a5149c59624b6")!

---

### Post by anderskitson on 2008-03-18
Awesome I got it to work, but I think It was something very dumb, I did everything for trouble shooting,still didn't work, but then i read the last line, and make sure you clear your browsers cache, and then it worked. What is xamp Im reading an oreiley book called learning php and mysql and the also mention xamp what does it replace, do i use one over the other?

---

### Post by Xiong Chiamiov on 2008-03-18
Ah yes, the old cache trick ;) .

XAMPP is basically a bundled version of PHP/apache/MySQL with a few other things, so that you only have to install one thing.  In Linux I found it to be only slightly useful, whereas on Windows it was very, *very* useful, since configuring all of those separately was a pain.  If you've got everything up and running, just keep it how it is.

And yes, O'Reilly ftw.

---

### Post by anderskitson on 2008-03-18
thank's you have been a great help, 
Solved

---

### Post by drubin on 2008-03-18
Well the appache is running.

You can see that by the fact that it is trying to download the file, via  [http://localhost](http://localhost). The fact that it is trying to download the php file, and not interpret it. is some config/ content type.

Trying looking in httpd.conf file (not 100% sure where it is located) for the line of mime types.

---

### Post by drubin on 2008-03-18
> **Chiko2008 said:**
> Thanks, rubinboy.
It helped me too :)

Pleasure.

---

