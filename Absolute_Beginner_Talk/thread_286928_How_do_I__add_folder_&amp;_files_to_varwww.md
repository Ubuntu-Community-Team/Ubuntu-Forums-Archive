---
title: "How do I  add folder &amp; files to /var/www/"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by kiwijor on 2006-10-28
Hi,

I have just installed Xubuntu in a new partition in a winxp-box, the install from an Iso I downloaded and burnt to CD went smoother than I vere imagined it would.

I needed to install apache2, Mysql, Php5, and phpMyadmin, that too went as smooth as!

But! Now I need to install Prado and my many years of ms-opsys never prepared me for the task, I have found /var/www/ but permission is denied me the opportunity of creating a new folder prado/ there, I have found Xarchiver but as above cannot extract to /var/www/

I have searched in vain for the explanation in the help files, but all I glean from them is that I need to be root to do the job, but there is no explanation of how I do that, I figure I need to use sudo in some way?

Everything so far has been so smooth, how can something so simple as modifing permissions be so hard for me!

In Vain I try-

kiwijor [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by PriceChild on 2006-10-28
I advise you add yourself to the "www-data" group via System>Admin>Users and Groups.

You could also use```
gksudo nautilus
```to move files... but be careful!

---

### Post by kiwijor on 2006-10-28
Hi, 

And thanks for the quick response.

I have added myself as a member of www-data but still have no permission to create folders or files in /var/www/

Kiwijor

---

### Post by Christmas on 2006-10-28
Just copy each file/directory you need on your web server using "sudo":
```
sudo cp filename /var/www
```
Or, for a directory:
```
sudo cp -r directory /var/www
```

---

