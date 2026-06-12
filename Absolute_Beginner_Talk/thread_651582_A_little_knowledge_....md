---
title: "A little knowledge ..."
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Joe Dinmore on 2007-12-27
I used to use Xampp on my Windows box, so I thought I could handle a LAMP just fine. Trouble is, I never could find MySQL to get it doing what I wanted, although it did find a database, and now I have stuffed it up completely (probably by changing paths, but I'm in such a mess now that starting over seems to be the best way forward.)
Please can someone tell me how to uninstall and subsequently reinstall MySQL? Apache2 and PHP are working, but I may have misconfigured one or the other of them as well.

---

### Post by SOULRiDER on 2007-12-27
Purge them
```
sudo aptitude purge <package1> <package2>...... <package-n>
```

---

### Post by Joe Dinmore on 2007-12-27
Thanks for that. 
So I "sudo aptitude purge apache2 mysql php5" then 
"sudo apt-get apache2 php5 mysql" then?

Where is the "thank you button" of which you speak?

---

### Post by taurus on 2007-12-27
You need to include the install option or apt-get will complain about it.

```
sudo apt-get update
sudo apt-get **install** apache2 php5 mysql
```

---

### Post by shearn89 on 2007-12-27
and the thanks button is the little starred medal at the bottom of each reply.

---

### Post by SOULRiDER on 2007-12-27
Aptitude is another package manager, just like apt-get but its actually better. So not only youc an remove/purge, you can also install like this
```
sudo aptitude install <package1>....<package-n>
```
Chech out the help and the man pages for more info
```
aptitude --help
```
```
man aptitude
```

The thank you button is the one that looks like [img]http://ubuntuforums.org/images/uf/buttons/post_thanks.gif[/img]. Use it whenever you feel you have to say thank you to anyone :)

---

