---
title: "phpBB installation help"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by cinmachina on 2007-05-20
Ok so I just turned my comp into a LAMP box, by using the following guide:

[http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/page-7.htm]("http://www.pcmech.com/article/windows-to-ubuntu-transition-guide/page-7.htm"):popcorn:

I have downloaded phpBB 2.0 (the most popular bulletin board system ever!) and extracted the contents to my public_html folder. I have followed the installation guide very closely, but I cannot get it to open the install.php file. When I try to open the install.php file, I am asked by firefox if I want to open install.php or download install.php. Obviously downloading it does nothing, and when I open it, i just brings me to a new tab, where I am again asked if I want to download it or open it.

Why can't I view this properly in firefox so I can configure my new bulletin board?

HELP!

---

### Post by Bachstelze on 2007-05-20
THis seems to be an Apache problem. Apache is treating PHP files like it would any other, and is not parsing them with the PHP module. Are you sure you installed it correctly ?

---

### Post by pbw on 2007-05-20
Make sure you've installed libapache2-mod-php5 and php5-mysql.

---

### Post by AnRa on 2007-05-20
You can install the packages 'phpbb2' and 'phpbb2-conf-mysql'

---

### Post by esoterica on 2007-05-20
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

> 
Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. Be sure to clear your browser's cache before testing your site again. 



phpBB is also the most heavily exploited bulletin board software in the world, I highly suggest you do a lot of reading up on security for this before opening it up to the public on your web server, and do not install it into any of the default named directories because the exploit bots will have a field day with you. I don't even have phpBB installed on my server and could show you my log files from the daily probes by script kiddies looking for phpBB on my server to execute the many known exploits on it.

Also make sure you in the very minimal utilize CAPTCHA with it or the spam bots will have a field day on your board as well. Out of the box CAPTCHA is not very effective anymore now that it can be defeated, there are probably third party scripts you can find for free that will enhance the now inefective CAPTCHA these board softwares use, I know there is at least for vBulletin Board in their third party .org forums, not sure about phpBB but there is probably the same.

---

### Post by cinmachina on 2007-05-21
> **pbw said:**
> Make sure you've installed libapache2-mod-php5 and php5-mysql.

Thanks guys, but unfortunately none of the solutions you have presented have worked for me so far. I did make sure those two packages were installed, but I'm still having the same problem. Isn't there anyone who can help me?

Yes I'm sure I installed them correctly according to the aforementioned guide as well.

---

### Post by EndPerform on 2007-05-21
> **cinmachina said:**
> Thanks guys, but unfortunately none of the solutions you have presented have worked for me so far. I did make sure those two packages were installed, but I'm still having the same problem. Isn't there anyone who can help me?

Yes I'm sure I installed them correctly according to the aforementioned guide as well.

To confirm you have PHP installed correctly, create a test.php.  Put this line in it:

```
<? phpinfo(); ?>
```

Then save the file.  Browse to where you put it ([http://localhost/test.php](http://localhost/test.php), for example) and if PHP is functioning properly, this file will display PHP configuration information.  If it attempts to download the file again, or if it displays the code in the browser window, something is wrong.  Before digging too deep into your configuration files, try a simple restart of the server by typing this into a terminal window:

```
sudo /etc/init.d/apache2 restart
```

After the server comes back up, try browsing to the test page again.  If it still trys to download the page or displays the text, something isn't configured properly.  I just recently installed apache / PHP / mySQL on a Feisty machine and it seemed to work ok.  Let us know what happens with this.

---

### Post by cinmachina on 2007-05-22
Thanks for the suggestion endperform. Unfortunately it still does not work. After I typed the above terminal sudo command, here's what I got:
```

apache2:  Could not fully determine the server's fully qualified domain name.
Using 127.0.0.1 for ServerName
apache2:  Could not fully determine the server's fully qualified domain name.
Using 127.0.0.1 for ServerName
                                                                                   [ OK ]

```


After this message, I tried to view test.php again, still no luck. Any suggestions?

---

### Post by cinmachina on 2007-05-24
Still no one to provide a solution?

---

### Post by who_cares on 2007-06-17
"apache2:  Could not fully determine the server's fully qualified domain name.
Using 127.0.0.1 for ServerName" shows when I start apache too, but the server still starts okay.
Check localhost and see if php is running now.

once you get php running you can get support for phpbb at phpbb.com

---

