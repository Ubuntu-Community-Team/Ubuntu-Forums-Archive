---
title: "php not working??"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by noelcal on 2007-11-07
Hi,
 I have installed PHP5 on apache2 in a UBUNTU 7.04 server . I tested the apache2 in the default folder and got an output "It Works" , but when i tried to test php by typing [http://localhost/php.test](http://localhost/php.test) i get the output 
# test.php
<?
	php phpinfo(); 
?>


and not the php page .

Can someone please help.

Thanks

---

### Post by LaRoza on 2007-11-07
> **noelcal said:**
> Hi,
 I have installed PHP5 on apache2 in a UBUNTU 7.04 server . I tested the apache2 in the default folder and got an output "It Works" , but when i tried to test php by typing [http://localhost/php.test](http://localhost/php.test)


That doesn't have the PHP extension, so it is not interpreted.

---

### Post by noelcal on 2007-11-07
oh sorry, i saved it as "test.php" not  php.test

---

### Post by carlosjuero on 2007-11-07
first thing I see wrong is the way your code is written, is that the exact output? if so then it should look like this: 
```
<?php
phpinfo();
?>

```

---

### Post by noelcal on 2007-11-07
> **carlosjuero said:**
> first thing I see wrong is the way your code is written, is that the exact output? if so then it should look like this: 
```
<?php
phpinfo();
?>

```


i took off #test.php and now i get the output as 

<?php
phpinfo();
?>

I guess i want to know why php is not interpreting the code i write and just displaying the code itself.

thanks

---

### Post by carlosjuero on 2007-11-07
> **noelcal said:**
> i took off #test.php and now i get the output as 

<?php
phpinfo();
?>

I guess i want to know why php is not interpreting the code i write and just displaying the code itself.

thanks
on the off chance, name the file test.php5

---

### Post by noelcal on 2007-11-07
> **carlosjuero said:**
> on the off chance, name the file test.php5

Same result 

<?php
phpinfo();
?>

---

### Post by carlosjuero on 2007-11-07
> **noelcal said:**
> Same result 

<?php
phpinfo();
?>
hmm, when you see the default Apache page (the one that tells you the installation was successful) do you see PHP 5 listed at the bottom of the page? (There should be an italic section that shows the Apache version, Perl Version, MySQL version, and PHP Version)

---

### Post by noelcal on 2007-11-07
> **carlosjuero said:**
> hmm, when you see the default Apache page (the one that tells you the installation was successful) do you see PHP 5 listed at the bottom of the page? (There should be an italic section that shows the Apache version, Perl Version, MySQL version, and PHP Version)

No, i don't see anything else . Actually when i type [http://localhost](http://localhost) i don't get anything on my browser, so i have to type [http://localhost/apache2-default/](http://localhost/apache2-default/)  then i get a result also i have to type [http://localhost/phpmyadmin](http://localhost/phpmyadmin) to get into the phpmyadmin page. 

Shouldn't all the folders be displayed when you enter the localhost address in the browser.

Thanks

---

### Post by noelcal on 2007-11-07
> **carlosjuero said:**
> hmm, when you see the default Apache page (the one that tells you the installation was successful) do you see PHP 5 listed at the bottom of the page? (There should be an italic section that shows the Apache version, Perl Version, MySQL version, and PHP Version)

sorry also to answer your question these are the details

Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c Server at 192.168.1.150 Port 80

---

### Post by noelcal on 2007-11-07
SOLVED 

I just added 

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
AddType application/x-tar .tgz

these three lines in httpd.conf and it works. Thanks for all your help.

---

