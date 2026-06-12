---
title: "Installing Python on Apache2: Error when starting Apache2"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by McKenna on 2006-11-07
I followed the Python install guide on this post:

[http://www.ubuntuforums.org/showpost.php?p=792999&postcount=3](http://www.ubuntuforums.org/showpost.php?p=792999&postcount=3)

It all works fine until I try and restart Apache2. I get the following error:

grep: /etc/apache2/mods-enabled/mod_python.load: Too many levels of symbolic links [fail]

Anyone know what the problem is here? :)

---

### Post by McKenna on 2006-11-07
I have managed to sort the problems with Apache and Python by simply re-installing libapache-mod-python2.4. I have run into another problem however, Python scripts run fine in the root directory of Apache /var/www/ but when I move up any directories (I'm installing trac, so the folder is /var/www/trac/) it simply serves the .py files as plain text. How do I get Apache to parse further up the folder structure?

Thanks for reading!

---

