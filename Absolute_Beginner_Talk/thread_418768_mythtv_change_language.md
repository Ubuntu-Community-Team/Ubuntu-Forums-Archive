---
title: "mythtv: change language"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by buddie on 2007-04-22
During the setup I accidentally choose a language that I cant understand.
I've tried uninstall, and install back anything that has to do with mythtv (even with the complete removal option), but I just can't get back the part where i can change the language setting.

Can anyone help? thanks.

---

### Post by dei on 2007-07-02
in short (advanced user) :
you login with any mysql-client (see below) into your database and then you can find in the database mythconverg a table called settings and in it an entry called Language, there you fill in for example EN.

Straight-forward-way in console:

mysql -u root -p mythconverg #replace root with your database user (default:root)

then enter your mysql-password and you get a promt like this:

mysql>

and here you enter:

UPDATE `settings` SET `data` = 'EN' WHERE CONVERT( `settings`.`value` USING utf8 ) = 'Language' LIMIT 1;

then you tap a:

quit;

and you're done.... hope i could help...

---

