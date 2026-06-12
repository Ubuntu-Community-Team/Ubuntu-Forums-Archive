---
title: "do not have write permissions"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by twp_twm on 2008-04-03
Have been trying to place an HTML file with a ".php" extension into the apache2-default folder at: /var/www/apache2-default but i keep getting the following message:

You cannot drop any items in a directory in which you do not have write permissions.

Can anyone help me out here please! Thanks in advance. TT

---

### Post by taavikko on 2008-04-03
```
sudo mv /file/you/want /where/you/want/
```

---

### Post by twp_twm on 2008-04-03
Have tried the following: sudo mv greetings.php /var/www/apache2 but keep failing?

---

### Post by taavikko on 2008-04-03
> **twp_twm said:**
> Have tried the following: sudo mv greetings.php /var/www/apache2 but keep failing?

I assume youre in the directory which contains greetings.php ?
then try
```
sudo mv greetings.php /var/www/apache2/
```

---

### Post by aysiu on 2008-04-03
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by twp_twm on 2008-04-03
I have tried using: sudo mv greetings.php /var/www/apache2/ but keep getting: is not a directory: no such file or directory.

The "greetings.php" file is stored in the Desktop folder.

Thanks for the link aysiu. Shall have a good read asap

---

### Post by aeiah on 2008-04-03
if the file is on your desktop then you'll have to navigate there first in the terminal. the terminal opens in your home folder by default so you'd have to change directory:
```

cd Desktop

```
and then use the other command. if you're regularly hacking around with files in your apache folder you might want to open a root nautilus window so you can edit and copy things around quicker. obviously, you have root priv so be careful.
do:
```

gksu nautilus

```
in the terminal

---

### Post by taavikko on 2008-04-03
> **twp_twm said:**
> I have tried using: sudo mv greetings.php /var/www/apache2/ but keep getting: is not a directory: no such file or directory.

The "greetings.php" file is stored in the Desktop folder.


Ok, then just mv it from the desktop to var/www/apache2/
```
sudo mv /Desktop/greetings.php /var/www/apache2/
```
You might want to check grammar on those files that they equals your files!

You could also use ```
gksudo nautilus
```
and cut&paste it to right folder. But I think we all prefer to do it in command line
so no bad accidents would happen;)

---

### Post by twp_twm on 2008-04-03
Have finally managed to drag and drop the "greetings.php" file into the apache2-default folder by opening a terminal and typing: kdesu konqueror. Now all remains is to successfully call and view it.

---

