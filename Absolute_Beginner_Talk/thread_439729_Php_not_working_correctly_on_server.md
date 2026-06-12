---
title: "Php not working correctly on server"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by icewindfalls on 2007-05-11
I am new to Ubuntu and new to Linux. I downloaded and installed on my web development server a copy of Ubuntu 6.06 LTS server as a LAMP server option. All the services are working correctly except for PHP. Any php script I try to access from a browser on an external system gives me this error:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/apache2-default/phpinfo.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


Can anyone help me? I have no idea what is wrong :(

---

### Post by octoberdan on 2007-05-11
> **icewindfalls said:**
> I am new to Ubuntu and new to Linux. I downloaded and installed on my web development server a copy of Ubuntu 6.06 LTS server as a LAMP server option. All the services are working correctly except for PHP. Any php script I try to access from a browser on an external system gives me this error:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/apache2-default/phpinfo.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0


Can anyone help me? I have no idea what is wrong :(

I'm not quite sure. You could try Ubuntu 7.04 Server or wait and see if anyone else responds. If no one does, then try posting in the General Help

---

### Post by Cypher on 2007-05-11
Do other regular .HTML files work in the "/var/www/apache2-default" directory?

What does your phpinfo.php file look like?

---

### Post by icewindfalls on 2007-05-11
Regular HTML files work perfectly. I get this error on any page with PHP.

Contents of phpinfo.php:

<?php
echo 'hello';
?>


That was merely a simple file I was using to test to make sure PHP was working. I also tried other PHP pages that I have written in the past for use on other servers, but nothing worked.

---

### Post by Cypher on 2007-05-11
I just installed LAMP on my machine and it worked right off the bat. Here are my commands:
```

sudo aptitude install apache2 php5-mysql libapache2-mod-php5 mysql-server

```
Then
```

sudo vi /etc/apache2/apache2.conf

```
Find the ServerRoot line and add:
```

ServerName localhost

```
This will get rid of the "Unable to determine fully qualified name" error.

Then I pointed my browser to "Localhost" and got the directory listing of "apache2-default", when I clicked on that, I got "It Works" so Apache was up and ready.

I then did
```

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/UserDir* .
sudo /etc/init.d/apache2 restart

```
This enabled the "public_html" directory in my home directory, then
```

cd ~/
mkdir public_html

```
I create the file
```

<?php phpinfo(); ?>

```
in index.php and when I pointed to http://localhost/~<username> I got the full PHP information.

---

### Post by icewindfalls on 2007-05-11
That worked! Thank you so much! I have spent so many hours lately waist deep in technical documentation trying to figure this out. Thank you!

Would I have to re-do the process if I want to serve pages from a public_html folder from another users home directory?

---

### Post by Cypher on 2007-05-12
You're very welcome.

And no, do you do not need to do anything special to have another user have his/her public_html work. They just need to create that directory and when you point to http://localhost/~<new username> it'll just automagically work.

---

### Post by icewindfalls on 2007-05-12
Unfortunately, now I have run into the same problem again :( I can still run PHP files directly from the public_html folder, but any PHP files in folders WITHIN public_html are giving me the same error that I got when I originally started this post. I need to be able to run a script from within multiple folder levels. There must be some configuration setting wrong somewhere...

---

### Post by icewindfalls on 2007-05-12
I solved my own problem. Since I am new to Linux I did not even think to look at the permissions associated with my files/folders. The whole problem was due to not having Read/Execute permissions set for the proper user. Now EVERYTHING works. :)

I feel silly for overlooking such a simple step. I still have a very microsoft mindset which I am working on breaking. I appreciate all the help, and I'm very excited about joining the Ubuntu/Linux community :)

---

### Post by jmwinn21 on 2007-05-30
I was having the same problem with my LAMP setup. Following the steps above solved it.
Thanks for the help.

---

