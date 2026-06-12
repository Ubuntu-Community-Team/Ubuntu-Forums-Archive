---
title: "Will the next Ubuntu release have PHP-Mysql"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by adamt222 on 2005-08-21
I know that the topic of adding MySql support to the on-board PHP was covered in other threads, but I looked at the instructions on how to do it and my head started spinning.

Isn't there any easier way to solve this?  If the upcoming release of Ubuntu could provide a PHP with MySql support already enabled, it would really help me as a programmer.  I already have a WIndows XP installation (on separate PC) and I was able to download and install a "WINLAMP" package that is a fully-integrated apache web server with Mysql and PHP all compiled together and good to go.

I would think Ubuntu would want to do the same thing,
either have Mysql support enabled in PHP, or at the very least, have some Ubuntu-specific instructions on how to set up LAMP properly so that it works.

Thanks;
Adam

---

### Post by DJ_Max on 2005-08-21
Once you start adding unneeded features & packages you start bloating the distro, and making the install longer. There are plenty instructions for installing PHP & MySQL. In the Wiki & ubuntuguide.org

---

### Post by adamt222 on 2005-08-21
"Once you start adding unneeded features & packages you start bloating the distro, and making the install longer. There are plenty instructions for installing PHP & MySQL. In the Wiki & ubuntuguide.org"

The guide explains how to install either or both PHP and Mysql, but not "PHP-Mysql". 

I appreciate the pointing to the forum discussion here, and tried a few of the things in there, it wasn't an intuitive venture. I was only inquiring to have this included in the distro so that users who needed to write PHP&Mysql pages could do so without having to do all these major steps.  Other distros do not pose this problem.

There is PHP included already in the distro, and there also is MySQL included in the distro, and you can easily install either, or both. But what is lacking is the "type of compiled" support for PHP-Mysql.  The PHP version, if compiled with support for MySQL in the original install shouldn't do any significant measure of bloating.

Speaking of "bloat", the install does not even ask if you want to install games on the install, and it installs tons of them by default.  I'm not "anti-game" but games should be a downloadable option in my opinion and not part of a major distro release.

---

### Post by Kvark on 2005-08-21
```
sudo apt-get php4-mysql
``` 
...then php and mysql will work together nicely.

---

### Post by DJ_Max on 2005-08-21
[QUOTE=adamt222]"Once you start adding unneeded features & packages you start bloating the distro, and making the install longer. There are plenty instructions for installing PHP & MySQL. In the Wiki & ubuntuguide.org"

The guide explains how to install either or both PHP and Mysql, but not "PHP-Mysql". 

I appreciate the pointing to the forum discussion here, and tried a few of the things in there, it wasn't an intuitive venture. I was only inquiring to have this included in the distro so that users who needed to write PHP&Mysql pages could do so without having to do all these major steps.  Other distros do not pose this problem.

There is PHP included already in the distro, and there also is MySQL included in the distro, and you can easily install either, or both. But what is lacking is the "type of compiled" support for PHP-Mysql.  The PHP version, if compiled with support for MySQL in the original install shouldn't do any significant measure of bloating.

Speaking of "bloat", the install does not even ask if you want to install games on the install, and it installs tons of them by default.  I'm not "anti-game" but games should be a downloadable option in my opinion and not part of a major distro release.[/QUOTE]
 You will need the MySQL bindings for PHP. Do what Kvark said.

I agree about the games, but they're included with Gnome. Most distro's include all the Gnome packages. There are some that modify them, by add/removing packages. This is OSS at it's best. I guess since Ubuntu is aimed at the desktop, they included it.

A good idea, would be to do what Gentoo does, and provide a *gnome-light* meta package, that will only install required Gnome packages.

---

### Post by adamt222 on 2005-08-21
Thanks DJMax and Kvark.

I've had sudo apt-get errors before though.
(I'll look around the forums for possible reasons why
it tells me "package #name# can not be found.)
I get that error after the command says "building package dependencies", etc.

I am going to reinstall the OS and see if these ideas work.

Thanks again for your helpful insights;

Adam

---

### Post by DJ_Max on 2005-08-21
[QUOTE=adamt222]Thanks DJMax and Kvark.

I've had sudo apt-get errors before though.
(I'll look around the forums for possible reasons why
it tells me "package #name# can not be found.)
I get that error after the command says "building package dependencies", etc.

I am going to reinstall the OS and see if these ideas work.

Thanks again for your helpful insights;

Adam[/QUOTE]
 No problem.
Also, before you re-install the OS, which probably is an overkill (this isn't Windows). Backtrack, and think what could have caused this, so it won't happen again. Such as using Debian repositories or .debs. Or forcing a package install.

---

### Post by Kvark on 2005-08-22
[QUOTE=adamt222]Thanks DJMax and Kvark.

I've had sudo apt-get errors before though.
(I'll look around the forums for possible reasons why
it tells me "package #name# can not be found.)
I get that error after the command says "building package dependencies", etc.

I am going to reinstall the OS and see if these ideas work.

Thanks again for your helpful insights;

Adam[/QUOTE]

Are you sure you have the extra repositories?
-> [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

