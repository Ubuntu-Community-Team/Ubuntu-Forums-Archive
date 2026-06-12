---
title: "LAMP server package"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by music_man on 2006-07-14
Hi

I went onto the Synaptics package manager and downloaded and installed PHP5, Apache 2, Mysql-client and phpmyadmin.

PHP doesn't seem to be running and I cant find the httpd.conf file to make it work...

Is there a bundled version of all these programs (like XAMPP) available in the package manager?

I would like to uninstall all those things I just installed, is there a log of what I did anywhere?

---

### Post by Frostmourne on 2006-07-15
In the Synaptic Package Manager, I think under the file menu there is a History option.

---

### Post by music_man on 2006-07-15
Cheers. I found it and am now just working through removing things. I would like to have a basic php, mysql and apache setup that work together. What should I download?

I think the Synaptic package manager should have a loading bar when one does a search. It appears to just stop and then it shows the search.

---

### Post by Frostmourne on 2006-07-15
[XAMPP]("http://www.apachefriends.org/en/xampp.html") I believe is one of the more popular LAMP distributions, it should suit your needs.

---

### Post by music_man on 2006-07-15
Yeah I downloaded that and I couldnt' figure out how to make it work. I used it on Windows before I installed Ubuntu.

---

### Post by Big_Al on 2006-07-15
Hey,

I'm trying to do the same thing at the moment. I'm totally new to all things webserver, so I'm going to follow the brief guide [here]("http://www.apachefriends.org/en/xampp-linux.html"). Let's see how I get on........

---

### Post by music_man on 2006-07-15
It's installed at /opt and I run the command line /opt/lampp/lampp start and it just does nothing.

---

### Post by music_man on 2006-07-16
-- deleted original post --

I got it going by doing this:

Went into terminal and typed su

I typed in my user password (which works for when I login to Synapics package manager). It didn't authenticate, which was weird, but I found this [http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu](http://www.ubuntux.org/how-to-change-the-root-password-in-ubuntu)

And made my own password (the same as my normal password)

I then managed to login as root and do /opt/lampp/lampp start

And it worked :)

Now I don't know how to stop the process...

---

### Post by music_man on 2006-07-16
Now how can I make that run on startup please?

I can't make an icon for the panel saying /opt/lampp/lampp start because I login as my user not root. I need to login under terminal to be able to start lampp I think.

---

### Post by dermotti on 2006-07-16
You might want to try Lighttpd, its a lighter and much faster webserver. I wrote a howto a few months back, EASY to setup.

[http://www.xubuntu.info/e107_plugins/content/content.php?content.10](http://www.xubuntu.info/e107_plugins/content/content.php?content.10)

---

### Post by music_man on 2006-07-16
Thanks for that.

I have xampp all set up now. I didn't need to edit any files and it has a securty check thing which is quite cool. It also comes with phpmyadmin which I like.

Any ideas on the startup?

---

### Post by sas on 2006-07-16
The proper way to do things is here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

make sure you keep up to date with any xampp security updates.

---

