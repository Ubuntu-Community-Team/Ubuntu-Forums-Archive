---
title: "Php?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by pipwicke on 2007-05-12
I really enjoy using and getting to know Ubuntu but was a little disappointed when i made a webpage "practice" and was unable to include a php script. Thought the php script would have been rendered no problem. Or have i done something wrong? Would appreciate any help and advice once again lol. Thanks all. pip 

<?php
echo "Hello World!";
?>

---

### Post by mendingo84 on 2007-05-12
well. to be able to run a php script, you have to install a web server at first, and then install php on your machine.
do the following:

```

sudo apt-get install apache2
```

```

sudo apt-get install php5

```

you could then create a "public__html" directory (name it that way, literally) and place it in your home directory. put your web project, including php, there and call them in the browser with smth like:

```

http://localhost/~youruser

```

---

### Post by hyper_ch on 2007-05-12
Well, you need to install apache, php and enable the php-module in apache and then you just need to put the .php file into the apache-web-dir (normally /var/www) and then you call it in the browser with "http://localhost/script.php"

---

