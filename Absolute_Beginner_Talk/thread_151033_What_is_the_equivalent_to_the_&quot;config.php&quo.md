---
title: "What is the equivalent to the &quot;config.php&quot; file in php5?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-27
Hello all !!!

I have been searching for this in other Forums too!!!

Whenever I search on how to enable ".html" parsing & "tags" & see that the answer is to look into the "config.php" file....

On the Terminal I perform a:

find config.php

And get nothing...

I also perform a:

locate config.php

And still get nothing...

What is the equivalent of the file "config.php" in "php" version 5?

Is it under a different file name?

Thanks.

---

### Post by oscar on 2006-03-27
I think that to parse files that end in .html with php you need to edit /etc/apache2/mods-available/php5.conf There should be a line:
```
AddType application/x-httpd-php .php .phtml .php3
```
just add .html to the end of it.
There is also a config file: /etc/php5/apache2/php.ini but I have never used it.
Perhaps you could describe what you are trying to do here?

---

