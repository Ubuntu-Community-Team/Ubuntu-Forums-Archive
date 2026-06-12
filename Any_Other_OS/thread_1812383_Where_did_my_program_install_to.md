---
title: "Where did my program install to?"
date: 2011-07-26
forum: Any Other OS
---

### Post by Worlds Tallest Engineer on 2011-07-26
Hi.  I'm trying to install WSUQ&T on Ubuntu 11.04.   It requires software that I installed using the "sudo apt-get install".  :P

```
sudo apt-get install php5
 sudo apt-get install apache2
 sudo apt-get install libapache2-mod-php5  
 sudo apt-get install postgresql
```


But now there are questions in the terminal that I don't know how to answer.  :confused:

```
Specify the desired WSUQ&T file directory (ie. /var/www/html/hwol): 
Enter the directory postgre is installed in (ie. /usr/local/pgsql): 
```


I have "/var/www" but not "/var/www/html/hwol".  Should I just make one, and put the files in it?

I have " /usr/local" but not " /usr/local/pgsql".  Should I just make one?  Where is postgre at?  Shouldn't "/usr/local/pgsql" be the default directory?

This software was developed on red hat.  Could that cause problems?

---

### Post by Peter09 on 2011-07-26
in a terminal you can type
 
```
locate <filename>
```
 
it will list all files with that name + path

---

### Post by Worlds Tallest Engineer on 2011-07-28
Thanks, this is a really cool tool. :)   But I'm not sure what to do with it. :(   I tried [locate postgre] and I got 847 hits.  I tried several other wordings and spelling.  However I am yet to figure out where postgre is installed.  

So, what should I be looking for? :confused:

---

