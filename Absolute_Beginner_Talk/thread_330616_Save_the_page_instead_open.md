---
title: "Save the page instead open?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by dujlinvik on 2007-01-03
Hi, i've just installed Apache2 in Ubuntu, have some web site made in PHP and Firefox does not display what it suppose to do....
instead of the contents of the page, the browser is offering to open the php script with 'gedit', or to save it to the disk.... i'm not an Apache expert, so i don't know where to start.......
any ideas?

---

### Post by MkfIbK7a on 2007-01-03
> the browser is offering to open the php script with 'gedit', or to save it to the disk
this means that the browser is trying to download it not view it
gedit is a text editor

---

### Post by dujlinvik on 2007-01-03
thanks for helping :) 
that's OK, but how can i 'force' the browser to display/view the content? ](*,)

---

### Post by MkfIbK7a on 2007-01-03
your browser probably cant view php files this is why its asking to download it so you can view it elsewhere

---

### Post by dujlinvik on 2007-01-03
i've viewed the same php script in the same browser (Firefox) with the same web-server (Apache) installed in Windows XP...

---

### Post by leep on 2007-01-03
It's not a browser nor php problem, it's a misconfiguration of apache2 (who does not know how to handle php files) on your machine. I'm experiencing the same problem. hope someone will help us.
S.

---

### Post by leep on 2007-01-03
Here is a discussion about this topic: [http://ubuntuforums.org/showthread.php?t=287876&highlight=apache+php](http://ubuntuforums.org/showthread.php?t=287876&highlight=apache+php)

---

### Post by dujlinvik on 2007-01-10
my problem was that i didn't have had installed the 'libapache2-mod-php5' package.... after installing this module, firefox is 'ready to show' my .php files as web pages! :p 
thanks for helping!

---

### Post by Palypup on 2007-01-10
I am running plain old 6.06 with default Firefox and when I find a page I'd rather save than bookmark, such as the one I am looking at right now -------                                   ([http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1962745](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1962745)
and it ends with dot php, Firefox will not open it up later even though it is the very same app that saved it in the first place.   If I am doing the same process with xp and friefox or 98 SE and Firefox, everything works the way I expect it to.
   So, how do I get Firefox to open a php file in Ubuntu?

---

