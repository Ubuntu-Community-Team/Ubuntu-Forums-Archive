---
title: "Wordpress Configuration - Please Help"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-04-19
I'm trying to set up a set up a site for my friend and he wants a bloggin section.

I got wordpress set up on my Ubuntu Server 6.06 and I can login and view the site just fine from my laptop on the same LAN as the Ubuntu Server. It works if I go to the domain blessedbyheart.com or if I directly go to my router's IP. It's strange though that when I navigate through the blog the domain name "blessedbyheart.com" changes to the server's LAN ip (192.168.1.111)

But if I try accesing from outside my LAN (ie: from my school) I cannot acces my wordpress section blessedbyheart.com/wp/.

Sometimes the HTML page loads, but the CSS and images do not.

If the HTML loads and I try to click on "login" for example the url changes from [http://blessedbyheart.com/wp/](http://blessedbyheart.com/wp/) to [http://192.168.1.111/wp/wp-login.php](http://192.168.1.111/wp/wp-login.php)

At the time of installing wordpress I had not given apache a ServerName in etc/apache2/apache2.conf
Could this be the problem?

Right now I've added the line 'ServerName blessedbyheart.com' within the apache2.conf but nothing changed. 

I also read somewhere about changing the /etc/hosts file by adding the domain to the line 
127.0.0.1	localhost
so that it would look like:
127.0.0.1	localhost blessedbyheart.com
This also didn't help though...

Do you suggest that I just re-install the Ubuntu Server and make sure to add the ServerName before the installation of wordpress?

Thanks very much if you can help.

Xarok

---

### Post by h0ax on 2007-04-19
Nothing is wrong with the Server side if you have it setup and you can see everything.

Your problem is DNS on the outside.

Your Wordpress Server is behind your local firewall, based on your 192.168.1.111 addresses.  
First: make sure you open port 80 for 192.168.1.111 on your router.
CHECK
Second: make sure you have your host set up to go to your external IP address.
(easy way to get this is [www.whatismyip.com](www.whatismyip.com))
CHECK
Third: If you have DSL you will want to install some kind of dydns on your server so that your DNS automatically refreshes when you get a new ip (DSL) - if you a static ip, which most cable providers offer - this may not be as pertinent.

Let me know how it goes and I will help further.

---

### Post by h0ax on 2007-04-19
Oh - and remove that line 
127.0.0.1 localhost blessedbyheart.com
from /etc/hosts/ - unnecessary

---

### Post by Xarok on 2007-04-19
Well, if I go to my IP [http://63.207.177.3/](http://63.207.177.3/) the main page works but the word press section [http://63.207.177.3/wp/](http://63.207.177.3/wp/) does not work outside my LAN.  This rules out the possibility that this is a problem with my DNS doesn't it?

When you access [http://63.207.177.3/](http://63.207.177.3/)  or [http://blessedbyheart.com/](http://blessedbyheart.com/) does the main page load?  It did earlier today at my school.

My problem is accesing the wordpress section of the site, not the entire site itself.

---

### Post by h0ax on 2007-04-20
The php works locally? Does it work remotely?
Put a test file 
> 
<?php
echo "Hello World!";
?>


put that in test.php and go to externally - does it work?

---

