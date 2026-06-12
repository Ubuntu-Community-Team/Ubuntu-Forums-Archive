---
title: "Problem starting phpmyadmin"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by hughc1 on 2007-08-20
I'm having  a problem with phpmyadmin.  First of all, let me list the software -

ubuntu – 7.04   desktop
apache2  2.0.55
mysql      5.0.22
php          5.1.2
phpmyadmin  2.8.0.3

Everything is installed with the add/remove tool if necessary.  The setups are defaults.
When I try to run phpmyadmin a blank page displays in firefox.  The starting page used is
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)  


I've applied this change from Docunentation.html-
[1.6] I can't use phpMyAdmin on PWS: nothing is displayed!
This seems to be a PWS bug. Filippo Simoncini found a workaround (at this time there is no better fix): remove or comment the DOCTYPE declarations (2 lines) from the scripts libraries/header.inc.php, libraries/header_printview.inc.php, index.php, left.php and libraries/common.lib.php. 
It didn't change anything.

I've added debug statements to index.php.  I stop getting output around line 107.  The script stops at 

// start output
header('Content-Type: text/html; charset=' . $GLOBALS['charset']);
?>
!!!!!!Nothing happens after this line!!!!!!
!!!!!!!!! notice the doctype lines are removed.!!!!!!!!!!!!!

<head>

A test script, as test.php, runs wonderfully.  Here is the script  -

<?php phpinfo(); ?>

 

phpmyadmin has been removed and reinstalled.  Can someone suggest a remedy?

---

### Post by indytim on 2007-08-20
I think phpmyadmin is using index.php vs index.htm.  Try to do the //localhost/phpmyadmin/index.php and see what happens.

IndyTim

---

### Post by hughc1 on 2007-08-21
Starting with [http://localhost/phpmyadmin/index.php](http://localhost/phpmyadmin/index.php) does not display a page.  The web page is blank.  The result is similar to starting with [http://localhost/phpmyadmin](http://localhost/phpmyadmin) 
There is no error added in apache2/error.log.
Thanks for your effort.

---

### Post by hyper_ch on 2007-08-21
does php work fine?

create a phpinfo.php
```

<?php phpinfo(); ?>

```
and run it in the browser.

---

### Post by hughc1 on 2007-08-22
The script-

<?php phpinfo(); ?>

works fine.  Thats what I used to test if php is working.

Thanks,


Hugh

---

### Post by hughc1 on 2007-08-31
How did I solve this problem?  Deleted Apache, MySql, and Phpmydmin.  Then loaded Xamp.  Now phpmyadmin works, apache works, and MySql works.  
Thank you Xamp folks.  Someone posted this suggestion in another post.

---

### Post by louieb on 2007-08-31
There is a nice how to in the tutorial section on xamp.  As you know xamp is for development only. If you want to take your server live then the easiest way to get lamp up and running is to use tasksel.
```
sudo tasksel install lamp-server
```
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

I've used both and did not have installation problems with either one.

---

### Post by Rick Z on 2007-09-07
I am able to display the [http://localhost/phpmyadmin](http://localhost/phpmyadmin) here is how...

are you able to see anything in the following URL? [http://localhost/](http://localhost/)
This shoudl display the Index of / which is what is listed in /var/www  I have 2 directories and one php file.

apache2-default
phpmyadmin
testphp.php

If you are able to just open up the [http://localhost](http://localhost), you should be able to navigate all the /var/www files or directories.

Now, I have a question that is related to phpmyadmin initial setup.  I went to the phpmyadmin website [http://www.phpmyadmin.net/documentation/#quick_install](http://www.phpmyadmin.net/documentation/#quick_install) and found the following task extremely confused...

cd phpMyAdmin
mkdir config                        # create directory for saving
chmod o+rw config                   # give it world writable permissions

Now, Which directory of phpmyadmin are we looking at?  Is this under /etc/phpmyadmin, /var/www/phpmyadmin, /var/lib/phpmyadmin, or /usr/share/phpmyadmin????  Maybe there's so other directories!!!  Well, what I did was that I went to /etc/phpmyadmin/ and did the task as the doc says, but when I refresh the [http://localhost/phpmyadmin/scripts/setup.php](http://localhost/phpmyadmin/scripts/setup.php) the "Configuration" section icon "Save" & "Load" are still grey out.  According to the phpmyadmin's doc or book, this should NOT be grey out once you mkdir config and set the premission.  I even bought the book Mastering phpMyAdmin 2.8 and the steps are similar, yet I can't get this setup.  

Can anyone please help me to the right direction.

---

