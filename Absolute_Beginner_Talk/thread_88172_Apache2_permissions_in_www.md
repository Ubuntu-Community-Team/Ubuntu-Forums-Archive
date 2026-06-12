---
title: "Apache2 permissions in www ?"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by zhorty on 2005-11-09
Hi guys.
I have installed apache2, but /var/www/apache2-default dir have some screwed up permissions, and I need to chmod every file to 777, to view it in the browser.

How do I fix this? If You don't know, how do I change the www root directory? I have checked the httpd.conf, but can't find any setting that changes the www root.

Need all help I can get!
Thanks.
- Fredrik.

**Edit:**
Ok, so I fixed the directory to all permissions (777) with sudo nautilus and go to properties, permissions etc etc.
But every file I upload have to be chmoded, to view it in the browser (I get 403 forbidden).

And btw, why the hell is the www root /apache2-default and not just /www ?
Thanks.

---

### Post by ametade on 2005-11-09
You don't need to chmod 777 all the files and directories. You can add yourself to the www-data group (System -> Admin -> Users and Groups -> Groups).

To change the webserver root edit the file /etc/apache2/sites-available/default

---

### Post by zhorty on 2005-11-10
Hi, and thanks for the answer!
I have fixed the www dir, added myself to the www-data, but still I get 403 forbidden in the browser.

Help anyone?
(Btw, the the www dir is in /home/X/www if that matters)

---

### Post by ametade on 2005-11-10
Check the /home/X/www directory's owner and permissions. The owner should be www-data and you should give read and write access to the www-data group:
```

sudo chown www-data:www-data /home/X/www
sudo chmod -R g+rw home/X/www

```
I Hope this can help you.

---

### Post by zhorty on 2005-11-10
Still don't work.
My user have full permission to the dir, and it's chmoded to 777. Still it seems like I have to chmod all files in it.

With other words, how do I do so that all files in the dir being chmoded to 777 ?

---

### Post by Susana on 2005-11-10
[QUOTE=zhorty]Still don't work.
My user have full permission to the dir, and it's chmoded to 777. Still it seems like I have to chmod all files in it.

With other words, how do I do so that all files in the dir being chmoded to 777 ?[/QUOTE]

chmod -R 755 dir
755 is usually enough

---

### Post by zhorty on 2005-11-10
Thanks, but it only chmoded the current files in the dir, if I copy a new file, I have to chmod the dir/file again :???:

**EDIT:**
GAH, JUST FORGET IT!
I forgot to edit the User and Group in apache2.conf to my username.
It's working just great now.

Anyway, thanks you all for help.

---

### Post by swing4 on 2005-11-15
[QUOTE=zhorty]Thanks, but it only chmoded the current files in the dir, if I copy a new file, I have to chmod the dir/file again :???:

**EDIT:**
GAH, JUST FORGET IT!
I forgot to edit the User and Group in apache2.conf to my username.
It's working just great now.

Anyway, thanks you all for help.[/QUOTE]

Hi, I'm new to this, so forgive my ignorance.
What is Group and how can i figure out what my Group is?

Can i leave www-data, or is this a security risk?

**Never mind**, didn't see this part
> You can add yourself to the www-data group (System -> Admin -> Users and Groups -> Groups).
:)

---

### Post by nucrebain on 2007-01-06
> **Susana said:**
> chmod -R 755 dir
755 is usually enough

FINALLY! Some one posts the correct answer! I now have acces to my website files! HAHAHAHAHA!

---

### Post by Rebajas on 2007-06-13
Just installed on Fiesty but looking at my groups, I don't have a www-data?

Any ideas - is there a good tutorial I can follow to set this up?


Cheers

---

