---
title: "troubleshooting php"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by jamil_1 on 2007-08-03
I have just started to learn php. I have installed  php5 and apache and few other dependencies however when ever I try to open a php file  firefox asks to download the file instead of interpreting the script. Any help ? I have read the similar threads but could not find the solution.

---

### Post by 505 on 2007-08-03
how are you opening the file with Firefox, locally. I presume you just double click. In that case the PHP is nothing more than a text file. You need to run it via your server. Make sure the PHP file is in your web root direcotry (I believe /var/www) then go to Firefox and enter [http://localhost/file.php](http://localhost/file.php)
If Firefox still want to open the file, the extension PHP is not registered as a filetype for PHP. In the PHP manual there is a good tutorial on how to configure PHP (although it should have been configured when installing it through the package manager)

---

### Post by apswartz on 2007-08-03
First, Make sure you are calling your php script via the web server and loading the file directly into the browser.

---

### Post by tbresson on 2007-08-03
If you just installed it you probably need to restart the apache server for it to work.

sudo /etc/init.d/apache2 restart

---

