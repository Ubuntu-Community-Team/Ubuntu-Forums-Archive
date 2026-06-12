---
title: "phpbb2"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by tbresson on 2006-09-06
Hi.

I installed phpbb2 on my Ubuntu.

First of all selecting the package phpbb2-conf-mysql does not help with EVERYTHING as promised. It simply creates the database for you.

You have to make a symlink to your /var/www yourself when you finally figure out where the installer put the files.

And googling it took hours ... anywayz, for those of you who had problems with this aswell, here's a great site that will help you - too bad it's hard to find and that the "just work" feature.. really doesn't work.

[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)

---

### Post by az on 2006-09-06
What do you mean?

That page clearly says you need to make the symlink - all you need to do is cut and paste the command:

Run this command to make the forum accessible through the web server 

sudo ln -s /usr/share/phpbb2/site /var/www/phpbb 

Please read /usr/share/doc/phpbb2/README.Debian for more details. 

Is that what you mean?

---

