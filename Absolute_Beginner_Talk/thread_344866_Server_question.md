---
title: "Server question"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by dandudeacal2000 on 2007-01-23
I am a beginner to servers, I know that they have a great deal to do with networking and web applications. I have a computer that is now running ubuntu desktop 6.06 LTS, could I install ubuntu server 6.06 on it or do you need a server. I don't know if there is a diffrence between a pc and a server. 

Thanks for any help

---

### Post by hyper_ch on 2007-01-23
The difference ist that between the Live and Server install different packages will be installed by default...
With the Live CD (and alternate) you get a GUI with it.... Gnome or KDE or Xfce and it's mainly aimed as desktop computer....

However a server does not need a gui and hence with the server install it would be considered as a waste...

You can easily install the packages that you need yourself to have a server and desktop computer...

Very like you will want to install:

Apache (web server)
PHP (web programming language)
MySQL (database system)

With those three things (plus some additional stuff like GD2 and/or ImageMagick) you can run most cms systems from your server/desktop---

---

### Post by mrsticks on 2007-01-23
Depends on the use.  I would say that if you are curious about a server ( web, database, email, etc... ) you could probably get away with using a basic desktop PC as your local server.  I run a small web development server, it was going to go into my buddy's trash.  A P3 700mhz Celeron, 512 MB RAM, 40GB HDD, runs my web and database server just fine.  

Obviously if you are talking a corporate environment, you might have to buy some good hardware to ensure nothing fails, no data is lost and so on.  I work for a smaller business, we have about 15 servers, half of them are linux ( mostly slackware, but newer ones are ubuntu ) and our hardware is nothing fantastic.  P4s, 40GB HDD, 1GB RAM.  And they run fine for our uses.

I wouldnt say you have to reinstall with server edition of Ubuntu though.  If you want to run a webserver, use the package manager and get apache, php, mysql ( or whatever DB ) and run with it.  Can you just format and re-install with server edition?  Probably.  Is it necessary?  Maybe not.

-peter

---

### Post by dandudeacal2000 on 2007-01-23
Ok, thanks for the help. I am trying to play around with mysql and php without cluttering up my friend's site, so the desktop version seems like the way to go. :D

I think I installed php apache and mysql but where do I find them. It seems the same to me installed or not. Do I have to do something with the terminal?

---

### Post by hyper_ch on 2007-01-23
I think the default location for the "webs" are /var/www

So just create a file

/var/www/index.html

and call it in your browser:

[http://localhost/index.html](http://localhost/index.html)

If that works, then you have found the right location of the apache web-docs...

and then create at the same place a file:

index.php

containing:

```

<?php phpinfo(); ?>

```

Call that in your browser:  [http://localhost/index.php](http://localhost/index.php)

If you get some output of installed stuff and such then apache and php run fine.

If not you may have to enable the php module first in the terminal:

```

sudo a2enmod php5

```

And then restart apache (also in the terminal)

```

sudo /etc/init.d/apache2 restart

```

---

### Post by dandudeacal2000 on 2007-01-24
I don't seem to have permission to make a new file in that dir, but when I login as root I do. But as root I cannot goto local host, I get permissions denied in the browser.

---

### Post by mrsticks on 2007-01-24
Obviously, as you have seen, it's all about permissions.

Your non-root regular user doesnt have the permissions to write to the htdocs ( or whatever dir your apache is looking at ) folder.  Naturally, sudo / root will have permissions, but the files root writes might not be readable by the user apache is running as.  Unless you make them 777 ( rwxrwxrwx ), which is not a secure solution.

Check the contents of your httpd.conf file, This should be in the /etc/apache dir by default.
In that file, you should have a couple of lines telling you who the server is running as:

```

User nobody
Group nobody

```

I run my server on another box all together, so I am just SSHing as http, the user apache runs as and editing my files like that.

In your case, you could sudo as the apache user and edit files like that.  vi would work, or you could start up your favorite editor as that user, and use that program.

```

$sudo su nobody
enter password
$nobody@localhost: vi index.php
OR
$nobody@localhost: bluefish &
launches bluefish ( or editor of choice ) and you can open, edit, save files as needed.

```

This might not be the best solution, but its the first one that popped into my head.

Or:

The sloppy, insecure solution would be to 777 the entire htdocs folder and everything in it, and that way everyone can read and write to it.  The security concern there is all too obvious.

Or:

You can configure apache to run as your normal day to day user, and problem solved.  

I dont work a lot in the gui, so take my advice as a grain of salt.

-peter

---

### Post by Bachstelze on 2007-01-24
What I personnally do is chowning /var/www to me and chmodding it 755. That way I and root have write access and everyone else has read-only access.

---

