---
title: "php first steps"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by abbrew on 2008-01-28
I think I have php, mysql, and phpmyadmin installed correctly. I want to write a php script, but I don't really know how. I looked at a few tutorials, and it seems easy enough, but I don't know how to get to the place where I type the code that becomes the php page that I can view.

---

### Post by emarkd on 2008-01-28
php is just code.  You can edit php in gedit, Ubuntu's default text editor.  It even supports syntax highlighting, so it's pretty good at it.

---

### Post by abbrew on 2008-01-28
Thanks. That's good to know. I am a true php novice though, and I was wondering if you could elaborate a little more. If I type a simple few lines of code (that would display "hello world"), how do I save it or make it so the code I entered in gedit can be viewed by my going to [http://localhost?](http://localhost?)

---

### Post by emarkd on 2008-01-28
Here's a very helpful script that'll tell you a lot about your install:

```
<?php
phpinfo();
?>
```

Paste that into a text document and save it as test.php.  Drop it into /var/www and point your web browser to [http://localhost/test.php](http://localhost/test.php)

---

### Post by scxtt on 2008-01-28
the file needs to reside in /var/www and be readable by "others" or have it owned by www-data as below ... if you call it index.html, just going to [http://localhost](http://localhost) will allow you to see it.
```
-rw------- 1 www-data www-data  739 Dec 17 20:57 test.php
```
[php]<?php
$hw = "Hello World!";
printf("%s", $hw);
?>[/php]

---

### Post by emarkd on 2008-01-28
Ah, I see your request for a hello world example now.  Try this:

```
<?php
echo "<center>Hello World!</center>";
?>
```

Save it as hello.php in /var/www and view it at [http://localhost/hello.php](http://localhost/hello.php)

---

### Post by abbrew on 2008-01-28
When I try to drop it into /var/www, it says I "do not have permissions to write to this folder." But thanks for the help, it is beginning to make more sense.

---

### Post by emarkd on 2008-01-28
yeah, you'll have to use sudo to move it there.  assuming it's on your desktop, go to the terminal and do 

```
sudo mv ~/Desktop/test.php /var/www
```

---

### Post by emarkd on 2008-01-28
By the way, after you do that, the easiest way to re-edit that file is to again use the command line because you'll have to use sudo to edit the file:

```
sudo gedit /var/www/test.php
```

---

### Post by Dr Small on 2008-01-28
I find that the easiest way to make / delete / browse and edit files is to open Nautilus with Gksudo and then browse to the www directory:
```
gksudo nautilus
```

Then when you edit files, it automatically opens them with Gedit with Gksudo, giving you complete permission to edit it.

Dr Small

---

### Post by emarkd on 2008-01-28
While Dr. Small is correct, make sure you're careful with that sudo nautilus session!  You can really mess up quick here by dragging/deleting the wrong thing.

---

### Post by Jeff250 on 2008-01-28
I would recommend against developing in /var/www.  Just create a directory named public_html in your home folder, e.g. /home/jeffrey/public_html.  Then you can get to this via [http://localhost/~jeffrey/](http://localhost/~jeffrey/).  This way you can do your development without needing root.  You can copy the files to /var/www when you are ready to go live or whatever.

---

### Post by Nythain on 2008-01-28
*cough*gksu gedit*cough*

but yeah, basically /var/www is usually owned by root, so in order to edit the files you have to do it as sudo, or gksu, or kdesu
also the advice of not actually playing around in /var/www is good advice, write your code in home, then copy it over with
sudo cp whatever.php /var/www
is safer, and umm... yeah

---

### Post by emarkd on 2008-01-28
Ok, I'll ask since you bring it up.  What is the difference between running sudo and gksu?  I know one asks for your password on the command line and one graphically, but in the end, what's the difference?

---

### Post by scxtt on 2008-01-28
there's no real difference to you or i, but in general gksu/gksudo is for GTK apps that you want to run as root ... as far as working w/ ~/public_html vs. /var/www goes: makes sense to use your ~ directory, but you can always use sudo (once) to make the file owned by your user, then you can edit it w/o sudo as much as you want w/o effecting anything else ... just need to make sure it's readable by "other" ...

---

### Post by apostate on 2008-01-29
Or, use sudo to make yourself a sandbox inside /var/www, and chown it to yourself:

chown yourname folder

Now you own this folder and can get into it without elevated privileges. 

PHP is cool, get yourself a book, and make sure apache is set to parse php. You only need to do this if going to [http://localhost/whatever](http://localhost/whatever) prompts you to download the file instead of showing it as a webpage. If your script makes a webpage (even a broken one) you are in business.

start any text file with <?php

...and put it in your web root, and apache will automatically try to parse it using the php processor.  Of course, the name should end with the .php extension.

Have fun!

---

