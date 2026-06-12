---
title: "php5 -&gt; php4"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by borland-c on 2007-01-03
In the beginning I install php4, then I decided install php5 - I do it
than I decided back to php4 I use command```
sudo apt-get autoremove php5
```and again install php4, after this php don't work, I try php5 - nope.
Now I cann't use php5 or php4

---

### Post by az on 2007-01-03
You can have both php4 and php5 installed at the same time.  The same instance of apache cannot easily use both at the samt time, though.  Whichever version of libapache2-mod-php you have installed will determine what apache2 uses.

To use php5, install libapache2-mod-php5

To use php4, install libapache2-mod-php4

Does this help?

---

### Post by borland-c on 2007-01-03
no, I use this command before
*libapache2-mod-php4 is already the newest version.*
but
*Apache/2.0.55 (Ubuntu) Server at xxxxxx.xxx Port 80*
without PHP

---

### Post by az on 2007-01-03
Please list all the apache and php packages you currently have installed.

---

### Post by FredSambo on 2007-01-03
your modules probably need to be enabled...

do:

```
ls /etc/apache2/mods-enabled
```

you should see, among other things:

```
php4.conf php4.load
```

if not, then you'll have to create a symlink from the /etc/apache2/mods-available directory.

---

### Post by borland-c on 2007-01-03
[I]install apache2
install php4
install libapache2-mod-php4[/I]
then I 
[i]install php5
install libapache2-mod-php5[/i]
after this I 
* autoremove php4*
now I can't install php5 or php4

---

### Post by FredSambo on 2007-01-03
> if not, then you'll have to create a symlink from the /etc/apache2/mods-available directory.

...you would do so, of course, by doing:

```
sudo ln -s /etc/apache2/mods-available/php4.conf /etc/apache2/mods-enabled/php4.conf

sudo ln -s /etc/apache2/mods-available/php4.load /etc/apache2/mods-enabled/php4.load
```

---

### Post by borland-c on 2007-01-03
fixed
thanks a lot  :rolleyes:

---

### Post by FredSambo on 2007-01-03
Awesome!

---

