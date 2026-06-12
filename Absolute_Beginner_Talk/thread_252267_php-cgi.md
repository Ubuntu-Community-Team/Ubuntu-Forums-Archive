---
title: "php-cgi?"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by hc2995 on 2006-09-06
I run a webserver BUt its not apache its called abyss web server X1 ([www.aprelium.com]("http://www.aprelium.com")) in order for me to get php support for my web server i need a file named php-cgi. I have installed php5 (It says "thank you for using php") now i need php-cgi BUT i cant find it! Does anyone run abyss and know how to correctly set-up php5 for abyss webserver?

---

### Post by hc2995 on 2006-09-06
no body?

---

### Post by shoot2kill on 2006-09-06
hi, i do not use the abyss, but try looking in ur PHP folder and in the bin subdirectory..

sorry, i used to setting up webservers on windowze.. :(

and, is it not possible to use apache..???

---

### Post by glycoknob on 2006-09-06
hi, 

sounds like you are looking for the php binary. 

you can install it with 

```
apt-get install php4-cgi
```

 - i'm sure there are also packages for php5 out there. you may have to add the universe reposities.

```
apt-cache search php cgi 
```

shows you the available php packages.

after installing the php4-cgi binary should be in /usr/bin directory.

according to abbyses setup instruction, this should do the trick.

HTH
martin

---

### Post by hc2995 on 2006-09-06
YES FINALLY! it works! php5-cgi was in the /usr/bin folder thanks!

---

