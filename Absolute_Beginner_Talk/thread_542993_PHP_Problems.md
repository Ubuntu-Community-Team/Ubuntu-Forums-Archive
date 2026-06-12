---
title: "PHP Problems"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by jazzdonkey on 2007-09-04
I am attempting to learn PHP and after installing apache 2 and php5 I started doing some examples from the book I am reading, however, when I save my file (phptest.php) and try to open it using Firefox I receive a window that states something along the lines of " this is a php script, how would you like to open it?".  The only option I have is Text Editor.  If I do try to open it again with Firefox I come right back to that window.  Can anyone help?

Thanks ahead of time.

---

### Post by KCPokes on 2007-09-04
I assume you went through the steps to install Apache and PHP5 from the repositories?  I also assume you are browsing localhost?  Normally the reason you see something like that is due to the web server not knowing how to handle a file with that extension (mime types).  Look in your mime.types file and ensure there is an entry for .php.

---

### Post by snowjm on 2007-09-04
when opening the file make sure that you are navigating to the correct url when you try to open it as well. ie [http://localhost/phptest.php](http://localhost/phptest.php)

In this case the file would be saved in root directory of where your web server points to.

---

### Post by afonic on 2007-09-04
You have to place it inside /var/www and open it like the user above suggested.

Just opening it through Firefox won't run it.

---

### Post by jazzdonkey on 2007-09-06
Hello,

Sorry for my lack of keeping you updated!  I tried putting the file in the ~/var/www file and then navigating to [http://localhost/phptest.php](http://localhost/phptest.php) and I still receive the same thing, a window that pops up and asks me what I want to do with the php script.  Choosing firefox to open it just puts it in a loop kinda and my other option is to open it in gedit.  I appreciate the help thus far! Can anyone think of what I could be doing wrong!?

Thanks!

---

### Post by hyper_ch on 2007-09-06
Did you actually enable the php5 module in apache?

```

sudo a2enmod php5

```

---

### Post by jazzdonkey on 2007-09-06
I don't know what I did exactly but I got it working.  I seemed to have had apache 1.3 and 2 so I completely uninstalled both apaches and php5.  Then I reinstalled apache2 and php5 and now everything works.  Thanks for everyone's help!  If someone could maybe explain what was going on that would be great!  Thanks!

---

