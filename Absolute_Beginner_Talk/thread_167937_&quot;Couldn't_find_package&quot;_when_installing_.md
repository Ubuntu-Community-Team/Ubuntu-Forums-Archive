---
title: "&quot;Couldn't find package&quot; when installing from Desktop"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by 3dd13 on 2006-04-29
I downloaded phpMyAdmin to my desktop and here's what happens:
edd1e@ubuntu:~$ sudo apt-get install phpMyAdmin-2.8.0.3.tar.gz
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package phpMyAdmin-2.8.0.3.tar.gz
The same thing happened with XAMPP, but I found a post to install the package that ships with Breezy, so I'm OK there. I verified spelling and case to no avail. This is only day 4 of using Linux for me, and my command line skills are weak until I learn what I'm doing. Do I need to specify a path if the file is on the desktop, or do I need to move the file to another directory before running the above command? I'll never be accused of being a genius, but this seems too simple to be this confounding to me.
Thanks for the help and the mercy.

---

### Post by mostwanted on 2006-04-29
Apt-get is not used for installing packages manually, it's used for installing apps from the Ubuntu repositories. Please read the guide linked to in my signature :)

PHPMyAdmin is available in the package *phpmyadmin* from the reps.

Edit: The URL in case someone digs up this topic and I've changed my sig: [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by 3dd13 on 2006-04-29
Thanks friend. I tried to search the forums, but as a n00b I don't know the language yet, so I most likely searched the wrong terms. Bookmarked your solution and I'm on my way to read it.
Much appreciated.

---

### Post by Biltong (Dee) on 2006-04-29
I know the feeling. I think I have bookmarked most of the important advice columns and this is another good one-
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
Have fun - I know I am!

---

