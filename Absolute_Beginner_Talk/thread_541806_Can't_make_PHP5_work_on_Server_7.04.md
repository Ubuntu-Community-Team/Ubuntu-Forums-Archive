---
title: "Can't make PHP5 work on Server 7.04"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by gotudor on 2007-09-03
i can't seem to make my PHP work on Ubuntu Server 7.04, i made the test.php page and load it into /var/www and when i click on it @ [http://localhost/](http://localhost/) it prompts to download the .php file instead of executing (i've installed LAMP)

---

### Post by jingo811 on 2007-09-03
I see that you stepped into the same bear trap as I did some months ago.
> i made the test.php page and load it into /var/www and when i click on it @ [http://localhost/](http://localhost/) it prompts to download the .php file
Instead of clicking on your php file you need to type the address location to it.  Like so:

```
localhost/test.php
```

If that doesn't work you probably need to change something in the apache2.conf file.  I don't remember which step that addressed this in my notes.  You can probably find it in the Official LAMP guide for more specific explanations.

[http://virtualseafarer.com/renaissance/desktop_lamp/chapter3.html#ch3](http://virtualseafarer.com/renaissance/desktop_lamp/chapter3.html#ch3)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

> 
Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. Be sure to clear your browser's cache before testing your site again.

---

### Post by 1oki on 2007-09-05
yeah I am having some trouble making php work with apache as well. I installed everything... run the "sudo a2enmod php5" and I get a "This module does not exist!". Any ideas?

a2enmod is there... but the php or php5 mod is not in the list when i type "/usr/sbin/a2enmod"... grrr... but i know php5 is installed... i guess i will retry it... Guess I should include that I am not using server... regular ubuntu ;) though... not much of a difference.

---

### Post by jingo811 on 2007-09-05
Did this work for you guys YES or NO?
> Instead of clicking on your php file you need to type the address location to it in your web browser. Like so:
```
localhost/test.php
```

If you're on Feisty 7.04 I'd recommend you read my notes on how I installed LAMP for Desktop from top to bottom it worked for me maybe it will also work for you.
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

---

