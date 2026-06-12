---
title: "PHP files cannot be viewed on web, but HTML can"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by Dee.Jarman on 2008-04-21
Hello all,

I am trying to get a server up and running publishing php pages.  The directory I am using contains both a html page and a php page, but only the html page is available on line.

I have done an ls -l and get the following results

-rw-r--r-- 1 root     root     3819 Jul  6  2007 index.html
-rwxr-xr-x 1 www-data www-data 2161 Jan 29  2007 setup.php

The index.html file can be seen, but I get an error 500 when I try to view the setup.php file.

Does anyone have any ideas on what is going wrong?

Thanks

Dee

---

### Post by WorldTripping on 2008-04-21
Sound like your php is not parsing correctly.

Have a look at this.

[https://help.ubuntu.com/7.10/server/C/php5.html]("https://help.ubuntu.com/7.10/server/C/php5.html")

---

### Post by WorldTripping on 2008-04-21
Also have a look at the logs:

/var/logs/apache2/

---

### Post by Dee.Jarman on 2008-04-21
Thanks World Tripping.

I have followed the page you suggested, but got stuck at
"By default, the Apache 2 Web server is configured to run PHP5 scripts. In other words, the PHP5 module is enabled in Apache2 Web server automatically when you install the module. Please verify if the files /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load exist. If they do not exists, you can enable the module using a2enmod command. "

These file are not present and when I enter the command a2enmod, it asks for a module name - do you know which one I should choose?

As to the logs,
The system error logs says
[Mon Apr 21 12:20:52 2008] [notice] caught SIGTERM, shutting down
Can't call method "disconnect" on an undefined value at /bin/mapssl line 84.
[Mon Apr 21 12:20:53 2008] [notice] Apache/2.0.55 (Ubuntu) mod_ssl/2.0.55 OpenSS                               L/0.9.8a configured -- resuming normal operations
[Mon Apr 21 12:27:03 2008] [notice] caught SIGTERM, shutting down
Can't call method "disconnect" on an undefined value at /bin/mapssl line 84.
[Mon Apr 21 12:27:05 2008] [notice] Apache/2.0.55 (Ubuntu) mod_ssl/2.0.55 OpenSS                               L/0.9.8a configured -- resuming normal operations


The error_log says
[Mon Apr 21 12:27:23 2008] [error] [client 79.73.87.74] File does not exist: /var/www/ilias3/setup/CBT2.gif, referer: [http://62.44.82.193/ilias3/setup/index.html](http://62.44.82.193/ilias3/setup/index.html)
[Mon Apr 21 12:27:23 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/ilias3/setup/index.html](http://62.44.82.193/ilias3/setup/index.html)
[Mon Apr 21 12:27:32 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd38 ***


Thanks again for your help with this.

Dee

---

### Post by madhusudancs on 2008-04-21
I will recommend you to go through this tutorial, [http://madhusudancs.info/LAMP-install]("http://madhusudancs.info/LAMP-install"). Please see the last parts of the tutorial where trouble shooting when PHP is not working is explained, if it doesn't work or if you do not get what you want to get I will be happy to help you out.

---

### Post by WorldTripping on 2008-04-21
Sorry for the delay, I was digging around.

Here is the Ubuntu How-To for LAMP:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

If I remember rightly, the contents of:
/etc/apache2/mods-enabled/
Are symlinks to:
/etc/apache2/mods-available/

So to enable new contents in /mods-enabled/, simply create a new symlink to the mod you require in /mods-available/

As madhusudancs says at the end of his blog, you'll need to open a terminal and type (when finished linking):
sudo a2enmod php5
/etc/init.d/apache2 force-reload

To update and restart Apache

The 'Can't call method "disconnect" on an undefined value at /bin/mapssl line 84.' error in your logs looks like a Perl or PHP error (? maybe !)

Personally, I would make the first file that I was working with do something like this:

```
<?php

phpinfo ();

?>

```

And call it index.php

And put it in the root of the webserver tat /var/www

That way you will be testing two things.

One is the php parsing, and two is the server set up to find .php as an acceptable index file.

The other error logs should disappear when you are calling / parsing a proper php file (I hope).

Hope this helps.

---

### Post by Dee.Jarman on 2008-04-21
Thanks again World Tripping,

I can now see both files in /etc/apache2/mods-enabled/, but it is still not working.  I have created a file called index.php and placed it in the /var/www/, but am getting the same problem.  i.e. index.html works, but index.php doesn't.  The contents of the error_log is shown blow

[Mon Apr 21 14:43:28 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 14:43:52 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/Trainers.jpg, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/TNA.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/Apropos_logo.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/Certification.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/CBT.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/TPM.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/ILT.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/Distance.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/CBT2.gif, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:43:59 2008] [error] [client 79.73.87.74] File does not exist: /var/www/.error, referer: [http://62.44.82.193/index.html](http://62.44.82.193/index.html)
[Mon Apr 21 14:44:04 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***

Thanks again for your perserverance with this

Mo

---

### Post by Dee.Jarman on 2008-04-21
sorry - I just realise a few of those error messages related to missing icons for the dummy html page I am using.  Its only the last error that relates to the php problem (I think).

Thanks

Dee

---

### Post by WorldTripping on 2008-04-21
From the log, Apache is unable to find a load of files:

TNA.gif
Apropos_logo.gif
Distance.gif

etc etc.

Do you recognise any of these files ?

Did you link mods/available to mods/enabled ?

Did you (in a terminal):
sudo a2enmod php5

Did you restart Apache ?

---

### Post by WorldTripping on 2008-04-21
oops..

overlap..

---

### Post by WorldTripping on 2008-04-21
Can you try to run the .php file a couple of times, and post the log.

There is both and 'access' and an 'error' log too.

---

### Post by WorldTripping on 2008-04-21
Also, could you post your httpd.conf file please.

---

### Post by WorldTripping on 2008-04-21
Also,

Post the .php file you are trying to parse.

---

### Post by Dee.Jarman on 2008-04-21
Just done again in case

root@ds5543:/var/log/apache2# a2enmod php5
This module is already enabled!
root@ds5543:/var/log/apache2# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                          [ ok ]
root@ds5543:/var/log/apache2#


but get the same problem.

I'm not sure if I have linked mods available to mods linked - could you tell me how I can do this.

I have copied the htppd.conf file below

./etc/apache2/httpd.conf
root@ds5543:/# cd etc/apache2/
root@ds5543:/etc/apache2# cat httpd.conf
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
root@ds5543:/etc/apache2#

The error log after attempting to load the page a few times is below
[Mon Apr 21 15:06:00 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:12:56 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:12:57 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:12:58 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:12:59 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:12:59 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:13:00 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***

The access log appears to be empty?

It feels like you are saving me from drowning here so thanks again for your help

Dee

---

### Post by Dee.Jarman on 2008-04-21
The index.php is as below

root@ds5543:/var/log/apache2# cd /var/www/
root@ds5543:/var/www# cat index.php
<?php
print_r (phpinfo());
?>

---

### Post by WorldTripping on 2008-04-21
Could you change the php file to contain:

<?php

phpinfo ();

?>

You shouldn't really be using ()'s with print:
[http://www.w3schools.com/php/func_string_print.asp]("http://www.w3schools.com/php/func_string_print.asp")

Let me know what you get.

---

### Post by WorldTripping on 2008-04-21
The httpd.conf is fine.

Sometimes you'll get errors if it is trying to load modules that are being loaded elsewhere. Not the case here.

Your modules look as if they are loading fine.

If changing the .php file dos not work, then I'm running out of ideas I'm afraid.

---

### Post by Dee.Jarman on 2008-04-21
Hi World Tripping,

I chnaged the file as below


root@ds5543:/var/www# cat index.php
<?php
print phpinfo();
?>

and restarted apache as a precaution.

The error_log I get is below
[Mon Apr 21 15:28:28 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:28:33 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:28:36 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:28:39 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
[Mon Apr 21 15:28:42 2008] [error] [client 79.73.87.74] *** glibc detected *** double free or corruption (fasttop): 0x0806fd40 ***
root@ds5543:/var/log/apache2#

Thanks again

---

### Post by WorldTripping on 2008-04-21
And the result if you just have:

<?php

phpinfo ();

?>

i.e. no 'print'

---

### Post by Dee.Jarman on 2008-04-21
Same thing unfortunately.

Error - 500

---

### Post by bartcramer on 2008-04-21
It is not going to help you immediately, but you could at least report that you're experiencing the same thing, more or less. 

[http://bugs.php.net/bug.php?id=44554](http://bugs.php.net/bug.php?id=44554)

---

### Post by WorldTripping on 2008-04-21
I'm afraid this is going to have to be my last guess.

You don't have two php's installed do you?  ie php4 and php5 ? If so, you should remove one before installing the other.

There are a lot of threads on the InterWeb about error like these and I'm afraid that none of them seem to have a straightforward resolution.

Sorry, but I'm fresh out of ideas.

Anyone else ?

---

### Post by WorldTripping on 2008-04-21
> **bartcramer said:**
> It is not going to help you immediately, but you could at least report that you're experiencing the same thing, more or less. 

[http://bugs.php.net/bug.php?id=44554](http://bugs.php.net/bug.php?id=44554)


There seem to be a few bugs being reported like this.

I couldn't find one that has a solution though.

---

### Post by Dee.Jarman on 2008-04-21
Hi World Tripping,

A guy I used to work with has had a look at the box and has managed to get it working.  I do not understand the resolution, but he tells me he did the following:

edited /etc/suphp/suphp.conf file
min_uid was set to 100
he changed it to 1
restrated apache and it worked.

Thanks again for your help.  It really did help me make progress - having access to such a great support tool is fantastic.  Thanks again

Dee

---

### Post by WorldTripping on 2008-04-21
Dee,

I'm happy that you got it working.

Gotta say though, that solution is completely out of my orbit of experience.

I've never had to use suPHP.

No problem for the attempted help, I'm trying to repay in kind all the advice I've been given over the past year.

:)

---

