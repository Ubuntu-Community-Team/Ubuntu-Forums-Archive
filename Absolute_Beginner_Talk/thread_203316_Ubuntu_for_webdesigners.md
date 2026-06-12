---
title: "Ubuntu for webdesigners?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by music_man on 2006-06-25
Hi

I have been looking at some threads:

[http://ubuntuforums.org/showthread.php?t=89690&highlight=graphic+design](http://ubuntuforums.org/showthread.php?t=89690&highlight=graphic+design)

[http://www.ubuntuforums.org/showthread.php?t=194146&highlight=php+mysql](http://www.ubuntuforums.org/showthread.php?t=194146&highlight=php+mysql)

[http://www.ubuntuforums.org/showthread.php?t=10465](http://www.ubuntuforums.org/showthread.php?t=10465)

Regarding whether or not it would be a good idea to do webdesign on Ubuntu. I am currently downloading the 6.06 desktop ubuntu to try out.

I would really like to use Ubuntu as my OS but as I have a few clients, I can't afford to muck around trying to find programs.

Programs I need are:

HTML tool - Has to have line numbers, not worried about WYSIWYG, possibly site manager. Any others aside from NVU, Vim and Amaya?

Graphics tool - I don't really like GIMP - having used it before. I would like somethign similar to fireworks for web graphics.

Apache, PHP and MYSQL - I would like it so they could just run as background services, so there are no tray icons etc.

Ideally I would like to be able to edit files in the HTML tool and view them in firefox on localhost.

Cheers

---

### Post by slider on 2006-06-25
Here's another thread for you.

[http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)

I started the switch to Ubuntu a couple of weeks ago. I have my old XP install in a vmware image and still use it for Photoshop which I can't do without. I've been using Bluefish which has "OK" syntax highlighting for php. It has a project manager built in that I haven't tried and I'm not sure about site management. The UI has a few glitches that are annoying enough that I'd like to find something else.

You'll have no problem running LAMP in the background. It took me about 4 days to get a useable development environment but am very happy I made the switch.

---

### Post by music_man on 2006-06-25
Thanks for your quick response.

Regarding LAMP. I looked here: [http://www.onlamp.com/](http://www.onlamp.com/) but it doesn't look very straightforward...

---

### Post by slider on 2006-06-25
LAMP == **L**inux **A**pache **M**ySQL **P**HP .

Basically apt-get is all you need to get them installed, configured and running. You can use the synaptic package manager which does the same thing with a graphical front end. The packages you need are:

apache2
lib-apache2-mod-php5
php5.0
php5-mysql
mysql-server
phpmyadmin

There may be a couple that I am forgetting just search for those packages in synaptic or us "apt-cache search". Once installed all you have to do is start putting files in /var/www and off you go.

---

### Post by closeyourwindows on 2006-06-25
the best editor for html is bluefish.  ```
sudo apt-get install bluefish
```  as far as graphics, gimp is just as powerful as PS, but you might want to look at opensource xara or Krita.

---

