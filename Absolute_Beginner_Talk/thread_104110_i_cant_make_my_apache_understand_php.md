---
title: "i cant make my apache understand php"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by bonusiso on 2005-12-15
both apace2 and php5 were installed to my pc but i cant make it working!!!

---

### Post by ape on 2005-12-15
have you installed apache or apache2?

There is a package for each Apache flavor that you need to install to get the mod_php5 apache module installed.

If you are running apache, install the libapache-mod-php5 package.
If you are running apache2, install the libapache2-mod-php5 package.

Once you've got these installed, you just need to edit your appropriate apache/apache2 config files to set up the php config you need.

---

### Post by Sheco on 2005-12-15
do you have libapache2-mod-php5 installed?

---

### Post by robotgeek on 2005-12-15
[QUOTE=ape]have you installed apache or apache2?

There is a package for each Apache flavor that you need to install to get the mod_php5 apache module installed.

If you are running apache, install the libapache-mod-php5 package.
If you are running apache2, install the libapache2-mod-php5 package.

Once you've got these installed, you just need to edit your appropriate apache/apache2 config files to set up the php config you need.[/QUOTE]

If you have apache2 installed, you can type "sudo a2enmod" to enable modules, and "sudo a2dismod" to disable modules. You also need to uncomment the appropriate lines in your httpd.conf to let apache recognize the php mime types.

---

### Post by NotJustANewbie on 2005-12-15
I found this website very good for all apache web-server related questions: [http://www.ricocheting.com/server/php.html](http://www.ricocheting.com/server/php.html)

---

### Post by bonusiso on 2005-12-15
@robotgeek thanks to you very very much :D it is working. 

but this time i cant use phpmyadmin

---

### Post by bonusiso on 2005-12-15
i need to control my database! how can i activate phpmyadmin

---

