---
title: "Ubunutu and PEAR"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by cconk01 on 2006-06-25
I have installed a LAMP server on an old laptop. I have installed squirrelmail and to my knowledge it is properly configured, except i cant login. when i do it tells me basically i need to have pear installed, which i thought was, anyways is there an apt-get command i can use to install it?

---

### Post by Kilz on 2006-06-25
[QUOTE=cconk01]I have installed a LAMP server on an old laptop. I have installed squirrelmail and to my knowledge it is properly configured, except i cant login. when i do it tells me basically i need to have pear installed, which i thought was, anyways is there an apt-get command i can use to install it?[/QUOTE]
I took a look in synaptic there is a pear package
```
sudo apt-get install php-pear
```
The command should work. But there are a lot of pear moduels. You might want to do a synaptic search for pear and look down the list to the php- entries and descriptions. [You could also go here and do the search.]("http://packages.ubuntu.com/") Then try 
```
sudo apt-get install <packagename>
```
for the ones you want installed.

---

### Post by cconk01 on 2006-06-26
ok - im pretty sure that i installed pear with php..... the error message is the same as it was before i installed it. Anyways it tells me i need to make sure pear is installed (which it is) and if it is then make sure the db.php file corresponds to the correct pear path.... where is this and where would the pear file be located?

---

### Post by cconk01 on 2006-06-26
anyone?

---

### Post by chiskop on 2007-06-30
cconk1 I'm no expert, but I'm setting up my development server at the moment and have been figuring this out.

Even after I installed php-pear, DB.php wasn't available. Like Kilz said you've got to: 
```
sudo apt-get install **php-db**
```

Then, make sure your paths are right in php.ini.

```
sudo gedit /etc/php5/apache2/php.ini
```

Look for the paths and directories info. Mine reads:

> include_path = ".:/usr/share/php:/usr/share/php/PEAR"

and see how you go with that.

---

