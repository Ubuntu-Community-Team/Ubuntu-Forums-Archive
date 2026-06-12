---
title: "Weird Apache Problem (Brain twister)"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Alcibiades Mystery on 2007-06-08
Running Ubuntu Feisty, with Apache , PHP5, and MySQL. Everything installed perfectly to /var/www, and I could see my directories at http://localhost/ . I then set up a folder in /var/www and installed Wordpress to it. Fine. Works great. Then I put another folder in /var/www and installed joomla to it. Perfect. My http://localhost then showed the following:

Apache --> http://localhost/apache2-default
phpmyadmin-->http://localhost/myphpadmin
(wordpress folder)-->http://localhost/wordpress
(joomla folder)-->http://localhost/joomla

All's right with the world. Then I tried drupal. I made a bit of an error. I unpacked drupal into my home directory, then moved it into /var/www. However, I didn't move it into the sub-folder, but directly into /var/www. So all the drupal files were in the main directory, and my http://localhost then defaulted to drupal. In other words, when I went to http://localhost in my browser, I got the drupal admin screen. Now, I could still access http://localhost/apache-2/ and http://localhost/myphpadmin and http://localhost/wordpress, etc. But I could no longer get the plain directory at /localhost. I could only get the drupal admin page.

OK, so I screwed up, and I thought I knew how to fix it. I scrubbed the drupal database, moved all the drupal files to trash, and reinstalled drupal in a sub-directory, /var/www/drupal. Yay. Great. That worked. Now my drupal page appears at http://localhost/drupal rather than at http://localhost. And now I should get the plain directory at http://localhost again, right? Wrong! Now when I go to http://localhost I get a 403 Error: 

Forbidden
You don't have permission to access / on this server.

I fiddled with all permissions to /var/www and /apache2-default. Nada. So what happened? I suspect that installing drupal to the /var/www directory changed permissions for apache. My problem is that I don't know which permissions, or how to change them back. I suspect it may be somewhere in the /conf/htaccess.conf file, but I really don't know. Any Apache geniuses out there have an idea of what I need to do to get back? By the way, all my sub-directories work perfectly still, and I can access all of them on the browser!:)

---

### Post by viciouslime on 2007-06-08
If you browse to that folder in nautilus and press ctrl+h to show hidden files, is there a ".htaccess" file? If so delete it.

---

### Post by Alcibiades Mystery on 2007-06-08
> **viciouslime said:**
> If you browse to that folder in nautilus and press ctrl+h to show hidden files, is there a ".htaccess" file? If so delete it.

You are officially my superhero.

My claims of "brain twister-dom" turned out to be brain twister dumb! Thanks. That worked perfectly. I think the volume of my writing on the problem compared to the volume of your writing on the simple solution are hilarious!

Thanks, vicious!:D

---

### Post by viciouslime on 2007-06-08
> **Alcibiades Mystery said:**
> You are officially my superhero.

My claims of "brain twister-dom" turned out to be brain twister dumb! Thanks. That worked perfectly. I think the volume of my writing on the problem compared to the volume of your writing on the simple solution are hilarious!

Thanks, vicious!:D

:p It did take quite some reading. I kept thinking I knew what you were about to say the problem was, then it would go on and say so i did x, y ,z etc.

Glad it worked for you :) Nice to be a hero.... :p

---

