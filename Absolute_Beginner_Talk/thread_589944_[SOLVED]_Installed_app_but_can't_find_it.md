---
title: "[SOLVED] Installed app but can't find it"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2007-10-24
Searched everywhere but can't find answer that works for me.

Feisty 7.04

Used Synaptic to install the package Wordpress from the repos. Installed successfully, but can't find the app in the Applications menu. 

Looked in Synaptic wordpress properties, but there are no installed files in /usr/bin, /usr/sbin or /usr/shared/bin

Typed "apropos wordpress" into terminal, but "nothing appropriate"

Typed "wordpress" into terminal: no file found.

Installed the Debian apps menu, but can't find that either :)

Where, or where has my wordpress gone? Any suggestions would be welcomed

---

### Post by earobinson on 2007-10-24
wordpress installed an apache server on your computer go to [http://localhost](http://localhost) and you should see a link.

---

### Post by SteveHoffmanUK on 2007-10-24
Thanks for the quick reply.

I clicked on the link and got the message "It works!"

Afraid this newbie doesn't understand the significance of having installed an apache server. How do I run wordpress?

Thanks again

---

### Post by Bloch on 2007-10-24
Are you planning to run your home computer as a server to serve a wordpress-based website to the web?
You will need to have your computer on 24/7 and if you get a lot of traffic your hosting service may object.


Or else you want wordpress to test it at home before deploying it on a commercial web hoster? 

This is what this guy uses it for

[http://ubuntu.philipcasey.com/13/07/2007/local-wordpress-in-ubuntu/](http://ubuntu.philipcasey.com/13/07/2007/local-wordpress-in-ubuntu/)

If you are a newbe then maybe you simply chose the wrong bit of software!! Wordpress is not for home use, it's for serving a blog to the internet.

---

### Post by SteveHoffmanUK on 2007-10-24
Bloch wrote:
*If you are a newbe then maybe you simply chose the wrong bit of software!! Wordpress is not for home use, it's for serving a blog to the internet.*

Bullseye!

Thanks for straightening me out. I certainly don't want to run my own server. I will explore further what I really do want . . .:)

---

