---
title: "problem opening or viewing PHP script"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by r3bol on 2007-08-04
I have a PHP file on a server that i am trying to open with gftp. When I try and view it with firefox (the chosen viewer i set up in gftp) i get a download dialog in firefox that asks if I want to open the PHP file in gedit, or if I want to save it to the disk. I tried to specify firefox from that dialog but it just tries the same thing in another firefox tab.
How can I fix it?

Thanks.

---

### Post by m0biu5 on 2007-08-04
If you download it to your computer, and you don't have Apache/PHP set up on your computer, then it will just download. If you view it online from the server, and the server has PHP set up, then it will execute the PHP file.

---

### Post by NoobieDoobieDo on 2007-08-05
I have apache and php installed and firefox still tries to save my local php files instead of opening them.

Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at localhost Port 80

---

### Post by fimbulvetr on 2007-08-05
One of three things is going on:

#1. You're incorrectly requesting the file.
#2. Your apache/php is setup incorrectly.
#3. Php is segfaulting on that script or some binary is corrupt.



If you make a file named info.php and put the contents:

```

<?php phpinfo();?>

```

and try to go to that, what happens?

If it works and you get a huge page about php stuff (like compile time, options, etc) then it's #3. Please do that so we can narrow it down.

---

### Post by NoobieDoobieDo on 2007-08-05
I already did that.  Firefox pops up the "what do you want to do" with this file window.

The default is set to "open with firefox" but if I go with that it simply opens another tab and ask me the same question.

---

### Post by fimbulvetr on 2007-08-05
NoobieDoobieDo, were you replying to me? You made a phpinfo(); file and it's the same symptoms (Asking you to download?)

Thanks

---

### Post by NoobieDoobieDo on 2007-08-05
fimbulvetr,

Yes, sorry I wasn't more clear on who I was speaking to.

I made the file you mention but firefox still won't open PHP files even though my [http://localhost](http://localhost) reports that both apache and php are running.

Thanks

---

### Post by fimbulvetr on 2007-08-05
Ok, good. Have you followed any kind of guide to get this working? I'm just tying to gauge which stage we're at. PHP files served from apache is a short process, but requires some steps, I want to see where you're at.

If not, can you explain what exactly you've done so far?

---

### Post by NoobieDoobieDo on 2007-08-05
apt-get install apache2
apt-get install php5 libapache2-mod-php5
/etc/init.d/apache2 restart

no errors during installation, browser reports both services are running.

Apache/2.0.55 (Ubuntu) PHP/5.1.6 Server at localhost Port 80

Thanks

---

### Post by fimbulvetr on 2007-08-05
Excellent. 

These files you're making, say info.php, where are you saving them? (i.e. in your homedir under /home/user)

---

### Post by NoobieDoobieDo on 2007-08-05
I was saving them to /home/me/Desktop

---

### Post by r3bol on 2007-08-05
I'm totally lost! :)
I thought I could skip the whole setting up apache, php, mysql by working on scripts uploaded to a remote host server. I'm using gftp and 100 web share (who offer php and mysql) for this. I selected firefox in 
gftp>FTP>Options>View Program: 
and when i right click the file and hit view firefox seems to be launching the php file from 
/tmp
and calling the file 
gftp-view.RrDumd.php
instead of 
php-test.php (<?php phpinfo(); ?)

I even tried 
[http://my-page-index/php-test.php](http://my-page-index/php-test.php)
but that just seems to redirect me to [http://www.100webads.com/](http://www.100webads.com/)

I still think this is possible this way. I need to figure out why its not running on the server, then I can figure out the gftp thing.

---

### Post by fimbulvetr on 2007-08-05
Noobie and r3bol are you the same people?

---

### Post by fimbulvetr on 2007-08-05
> **NoobieDoobieDo said:**
> I was saving them to /home/me/Desktop

Ok, Noobie, you're close but missing one thing:

Apache only serves files from the directory you tell it to. By default, it looks for files in /var/www.

On my workstation, I just did:

```

sudo apt-get install apache2
sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

```

Just like you, then I did:

```

sudo mv ~/Desktop/info.php /var/www/info.php

```

Then I went to [http://localhost/info.php](http://localhost/info.php) in firefox and it worked.

So you need to place your php files in /var/www/ directory.

Note that by default you don't have access to write in this directory. You can change this by doing:

```

sudo chmod 775 /var/www/
sudo chown `groups | awk '{print $1}'` /var/www

```

Then with your editor of choice just open, save, edit and delete files by browsing to /var/www/ directory.

---

### Post by fimbulvetr on 2007-08-05
> **r3bol said:**
> I'm totally lost! :)
I thought I could skip the whole setting up apache, php, mysql by working on scripts uploaded to a remote host server. I'm using gftp and 100 web share (who offer php and mysql) for this. I selected firefox in 
gftp>FTP>Options>View Program: 
and when i right click the file and hit view firefox seems to be launching the php file from 
/tmp
and calling the file 
gftp-view.RrDumd.php
instead of 
php-test.php (<?php phpinfo(); ?)

I even tried 
[http://my-page-index/php-test.php](http://my-page-index/php-test.php)
but that just seems to redirect me to [http://www.100webads.com/](http://www.100webads.com/)

I still think this is possible this way. I need to figure out why its not running on the server, then I can figure out the gftp thing.

r3bol, I just finished helping Noobie, so I'll help you now.

Let's step back and not use the remote server and just try to get them working locally first so we can keep things simple.

What steps have you done so far?

---

### Post by r3bol on 2007-08-05
apache and php are now installed!

to get into /var/www I did like you said...

sudo chmod 775 /var/www/
sudo chown `groups | awk '{print $1}'` /var/www

I made php-test.php again and [http://127.0.1.1/php-test.php](http://127.0.1.1/php-test.php) works! 

That was cool because I didnt know you could change the local directory access like that although I have no idea what *sudo chown `groups | awk '{print $1}'` /var/www* means :)

Anyway, I tried gftp again and it gives me the save dialog box again awwwwwwwwwwww. (i get the redirect if I try the www url)

What do you think?

---

### Post by fimbulvetr on 2007-08-05
> **r3bol said:**
> apache and php are now installed!

to get into /var/www I did like you said...

sudo chmod 775 /var/www/
sudo chown `groups | awk '{print $1}'` /var/www

I made php-test.php again and [http://127.0.1.1/php-test.php](http://127.0.1.1/php-test.php) works! 

That was cool because I didnt know you could change the local directory access like that although I have no idea what *sudo chown `groups | awk '{print $1}'` /var/www* means :)

Anyway, I tried gftp again and it gives me the save dialog box again awwwwwwwwwwww. (i get the redirect if I try the www url)

What do you think?

Well all this:

sudo chown `groups | awk '{print $1}'` /var/www

means is take the output from ```
groups | awk '{print $1}'
```

and put it in the line 
```

sudo chown "output" /var/www
[code]

I messed it up though, but it still worked. In the future, use this one instead though:

sudo chgrp `groups | awk '{print $1}'` /var/www

It was only by shear fortune of ubuntu primary group being the same as your username that it worked.

Anyway, so you're working locally, now you're trying to get your remote server to work, right?

What is the remote server, as in, is it a hosting server you pay for or a friends server or your network, etc? Has it successfully run php before?

P.S. Don't worry about this behavior:

[code]
I even tried
http://my-page-index/php-test.php
but that just seems to redirect me to http://www.100webads.com/
```

It's just a nuance of firefox doing a Google "I'm feeling lucky" search for the string you entered in if it's an invalid domain, and [http://my-page-index/php-test.php](http://my-page-index/php-test.php) is an invalid domain.

---

### Post by r3bol on 2007-08-05
Its [http://www.100webspace.com/](http://www.100webspace.com/)
with
• PHP, Perl/CGI-BIN
• FTP Access
and some other features.

Hosting service. You are meant to be able to run php scripts from anywhere (just needs file + folder permissions to be 755).

---

### Post by fimbulvetr on 2007-08-05
Oh I see, well then I was wrong about the thing just being a nuance of firefox, it's actually something to do with your webhost.

I'm afraid I'm not sure what to tell you. When you gftp into your account, what files/directories do you see? Generally you will have a folder named www or public_html or something. When you put files under there it should be accessible on the web.

---

### Post by NoobieDoobieDo on 2007-08-05
Thanks for the help.

When I moved the php.php file to /var/www and then try to open it via firefox I get the same effect.  I attached a screen shot for your viewing pleasure.

[Screen shot]("http://img259.imageshack.us/img259/7793/screenshot15hp5.png")

When I chose the default action (open with firefox) it just opens a new tab and ask the same question.  In the screen shot I told it to open about 4 times just to make the effect clear.

Thanks for the help but my need to run apache and php is gone (trying to simulate my web hosting which was temporarily down).

Here is my php.php file which is located in /var/log

[PHP]<?php phpinfo(); ?>[/PHP]

Good luck to anyone else who has this issue.

---

### Post by m0biu5 on 2007-08-05
Did you execute the following command?
```
sudo a2enmod php5 
```

A little reading always helps: [https://help.ubuntu.com/community/ApacheMySQLPHP#head-59bdeb1f6438eddbde544b41ca0a5149c59624b6](https://help.ubuntu.com/community/ApacheMySQLPHP#head-59bdeb1f6438eddbde544b41ca0a5149c59624b6)

Also, you should enable user directory access (localhost/~username from ~/public_html/) with the userdir mod. 

I think the following code will enable that: 
```
sudo a2enmod userdir
```

---

### Post by avik on 2007-08-05
Also, are you sure you're using [http://localhost/php.php](http://localhost/php.php), instead of file://var/www/php.php?  That makes a difference.

---

### Post by r3bol on 2007-08-06
> When you gftp into your account, what files/directories do you see?hmm thats intresting. gftp displays only the files and folders i have created ie index.html etc...
but the web based filemanger at 100webshare says I have logs, mail and www as my err, top view folders (is that what you call them when you cant traverse any further outside?)

My stuff is in www in 100WS

---

