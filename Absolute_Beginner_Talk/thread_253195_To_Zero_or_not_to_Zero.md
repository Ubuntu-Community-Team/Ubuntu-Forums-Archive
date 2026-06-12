---
title: "To Zero or not to Zero"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by YeahBuntu on 2006-09-07
So for 4 days now I have been runing strictly Ubuntu

I intended to setup a webserver on this baby to learn asp perl php python.. whateva suits my fancy...

I did not realize that the server install was a totally different ISO.

A year ago when I tried to install/learn linux I failed miserably and whenever I went to reinstall and start over the install would stop.  The only way to "start fresh" was for me to use the gwscan program disc to write zeros to the whole drive and start new.

I am currently runing Dapper(im so proud of myself) and am wondering if I should zero the sucker and follow one of the many [guides]("http://howtoforge.org/lamp_installation_ubuntu6.06") i've found for installing a webserver using the server installation ISO?

Or .. do I try to muddle my way doing it with my current installation?  As a side note.. after Ubuntu downloaded a plethora of updates I now have.. like 4 options in Grub to load Ubuntu .. is this normal?

---

### Post by jordanmthomas on 2006-09-08
There is no reason you can't install all the servers you want in the desktop version of Dapper.   The only real difference in the desktop and server editions is that the server edition doesn't install a GUI.  

In fact, the guide you linked to has you install the desktop version, so you're already ahead of the game.

---

### Post by YeahBuntu on 2006-09-08
Thanks much jordan .. about the grub thing... is that normal?

---

### Post by jordanmthomas on 2006-09-08
Oops, forgot to answer that part.

Yes, that is perfectly normal.  When you updated, you installed a new kernel and the old versions hung around just in case the new one doesn't work right.

---

### Post by DSn0wMan on 2006-09-08
Setting up LAMP (Linux, Apache, MySQL, and Perl/PHP/Python)is very easy with the server install disc as there is an option to make it a LAMP server.

On the other hand there is nothing stopping you from installing all the server stuff you need on your desktop install.

If you want to use asp you will need to install mod_mono for apache, and you'll probably want mono dev package.

All the packages you need are available in the repositories.

---

