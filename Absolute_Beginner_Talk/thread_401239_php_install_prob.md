---
title: "php install prob"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by RED WIND on 2007-04-04
I try to install php using
```
sudo apt-get install php4
```

and it doesn't seem to find it does anyone know what I am doing wrong

---

### Post by indytim on 2007-04-04
Follow this verbatum and your LAMP will be "lit".

[LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP")

IndyTim

---

### Post by Bachstelze on 2007-04-04
What do you want to use PHP for ? Apache mod, CLI, CGI ? If it's for Apache 2, do

```
sudo apt-get install libapache2-mod-php4
```

---

### Post by RED WIND on 2007-04-04
jits for apache but I need php b4 I can use the mod

---

### Post by Bachstelze on 2007-04-04
Installing the mod will install PHP itself too, thaks to the magic of apt :)

---

### Post by RED WIND on 2007-04-04
ok php5 works

---

### Post by az on 2007-04-04
Being that php4 is a security nightmare, it has been removed from the feisty archive.

Only php5 is in Ubuntu starting from Feisty.  

Relax!  Php4 is still in Dapper and will continue to be there until Dapper is retired.

---

### Post by kimu on 2007-04-20
> **az said:**
> Being that php4 is a security nightmare, it has been removed from the feisty archive.


Maybe php4 is a security nightmare, but I think it's our choise, not Ubuntus',  to decide if use it or not.  
WEB DEVELOPERS NEED IT!!!!!!!!

Put the package in the repository! I don't want to roll back the entire system reinstalling dapper or edgy only for a single package, otherwise Feisty will be the first linux distribution marked as "Not for web developers".

Pls, give us some advice of when the package will be put in the repository again.

---

### Post by thebrade on 2007-04-20
totally agree w/ kimu. as a web developer, I run php5 as a module but I have to run php4 as CGI for certain software we work with. certainly we should have the choice to install it.

---

### Post by Bachstelze on 2007-04-20
> **kimu said:**
> Maybe php4 is a security nightmare, but I think it's our choise, not Ubuntus',  to decide if use it or not.  
WEB DEVELOPERS NEED IT!!!!!!!!

Put the package in the repository!


It's Ubuntu's choice, not yours, to decide what is in the Ubuntu repositories. You're free to build PHP4 from source if you want it, are you not ?

---

