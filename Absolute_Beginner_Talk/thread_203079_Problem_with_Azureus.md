---
title: "Problem with Azureus"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by measure on 2006-06-24
Hi all :)

The error popup at the bottom of my monitor wont disappear after I close azureus or even if I click "Hide" or "Hide All". I've attached a SS and any advice would be greatly appreciated.

thanks

---

### Post by mlind on 2006-06-24
[https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813)

You'll have to install CVS build of Azureus2.jar

---

### Post by measure on 2006-06-24
Can you explain how to do it? I'm having some trouble :)

---

### Post by mlind on 2006-06-24
[QUOTE=measure]Can you explain how to do it? I'm having some trouble :)[/QUOTE]

You'll have to locate Azureus2.jar

```

sudo updatedb
slocate Azureus2.jar

```

I think it's located on /usr/lib/Azureus. Download current CVS build from 
[http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php) and replace Azureus2.jar

```

cd /usr/lib/Azureus
sudo wget http://torrents.aelitis.com:88/files/Azureus2403-B46.jar
sudo mv Azureus2.jar Azureus2.jar.orig
sudo mv Azureus2403-B46.jar Azureus2.jar

```

You can also do replacing by opening nautilus with root privileges using *sudo nautilus*,
then copy paste new Azureus2.jar to /usr/lib/Azureus. Just make sure you take backup
of the original before replacing.

---

### Post by measure on 2006-06-24
Thank you, that worked perfectly. Although it wasn't in the directory you mentioned it wasn't hard to put it together. 

thanks ! :)

---

### Post by Drakkor on 2006-06-24
Another problem Azureus related:

---

### Post by Drakkor on 2006-06-24
I have tried to uninstall and reinstall Azureus, same problem !

---

### Post by Epperly on 2006-07-20
Thanks for the hide fix mlind!

---

