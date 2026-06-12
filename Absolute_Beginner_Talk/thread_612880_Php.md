---
title: "Php"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by sabrina on 2007-11-14
Hi all!

I can't figure out how to setup PHP in Gutsy Gibbon.

I've made this simple test.php file:

<?php
echo "Hello world!";

?>

But when I try to open it in a browser, it won't display it. It suggests to view it with my default editor or to download it.

Can anyone help me?

---

### Post by smartbei on 2007-11-14
Have you installed php and apache?

If so, make sure that the file is in your www directory (ususally /var/www) and browse to it ina  web browser using http://localhost/<your file>.

If not, see [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) and follow the instructions for Feisty.

Hope that works out.

---

### Post by sabrina on 2007-11-14
Thank you so much! :D

I didn't know, that I had to place the file in /var/www/

Can I change that path to /home/myUsername/files ?

---

### Post by louieb on 2007-11-14
> **sabrina said:**
> ...t I had to place the file in /var/www/
Can I change that path to /home/myUsername/files ?
Theres a couple of ways. Symlink is one or set up a virtual host. and put you site in ~/public_html.  
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")
to help w/setup may want to look at webmin too.

---

