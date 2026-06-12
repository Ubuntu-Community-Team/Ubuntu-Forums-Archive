---
title: "Apache server, so where are my files located?"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by gotquestions on 2007-03-16
I am trying to install LAMP and I just installed Apache server.

sudo apt-get install apache2
Then I tested with this: * [http://localhost](http://localhost) yay! It works is what it says. 

Now that I know localhost url works, I see a "apache2-default/" folder. 

Can someone tell me where that folder is located in my computer?
How can I add more files to where I can see files on that [http://localhost](http://localhost) spot?

---

### Post by dfreer on 2007-03-16
/var/www is the default directory for apache. the apche2-default folder you see is located at /var/www/apache2-default. So basically, anything you put in /var/www will be visible from [http://localhost](http://localhost)

---

### Post by taimel803 on 2007-04-17
how to copy mysite to /var/www
 it show "not permission"

---

### Post by darkrose on 2007-04-17
Just give yourself permission to read/write to the directory.
Open a terminal and run:
sudo chmod -R o+rw /var/www

Or, add your self to the group that owns the folder:
sudo usermod -Gwww-data yourusername

---

