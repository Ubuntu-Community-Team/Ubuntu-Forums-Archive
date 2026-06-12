---
title: "apache PHP help"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Clipz on 2006-03-12
Hi all
i just installed apache on my computer and i tried to install php but when in make  a file call testphp.php in my www folder and i try it with localhost/testphp.php the page does not come up.

---

### Post by mlind on 2006-03-12
if apache webserver works okay, you should enable debug output logging on
your php configuration file and make a .php file containing only following piece of
code:

```

<?php
    phpinfo();
?>

```

also, look apache's log entries /var/log/ to see it's not permission related.

---

### Post by Clipz on 2006-03-12
its stil not workking it wont open the page in the browser it makes me download it

---

### Post by mlind on 2006-03-12
apache doesn't seem to recognize php extension.
are you using php version 4 or 5?

does a2enmod command list any php modules?

---

### Post by Clipz on 2006-03-12
i got php to work but i cant edit any thing in the www folder llike i cant delete files

---

### Post by Clipz on 2006-03-12
i think i need to change the permissions in the apache2.conf thing

---

### Post by mlind on 2006-03-12
It's better to enable userdir module, so you can do development locally.

```

sudo a2enmod userdir
mkdir ~/public_html

```

then edit your files on public_html directory instead.

to access the files using web-browser, go to url
[http://localhost/~username/](http://localhost/~username/)
where username is your ubuntu username

---

