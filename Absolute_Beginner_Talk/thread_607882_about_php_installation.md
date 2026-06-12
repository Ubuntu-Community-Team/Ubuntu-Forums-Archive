---
title: "about php installation"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by tejasrameshbhai on 2007-11-09
hi all , i m new to linux

i have installed  php,  apache and mysql 
but when i make .php file in var/www folder then it gives me error that  i have not permissions to create folders ...

 so , what i should do . in order to fix this problem and make php working fine....??
plz help me ...
Thanks in Advance.....

---

### Post by jingo811 on 2007-11-09
Never fear I is here.
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html](http://virtualseafarer.com/renaissance/desktop_lamp/index.html)

---

### Post by carlosjuero on 2007-11-09
by default /var/www is assigned to root for permissions; you have 2 ways to go about this - you can change the permissions on the main web root, or you can create a sub folder as root and set permissions for your user.

Use the Terminal for the following examples (one or the other) [Applications -> Accessories -> Terminal)

Option 1: Change the main /var/www to be accessible by you.
```

sudo chown <user name> -R /var/www
sudo chmod 755 /var/www

```

Option 2: Create a sub folder for your user to be able to use
```

sudo mkdir /var/www/myroot
sudo chown <user name> /var/www/myroot
sudo chmod 755 /var/www/myroot

```

---

