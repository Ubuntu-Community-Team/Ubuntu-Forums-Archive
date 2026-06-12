---
title: "Ubuntu/Apache -- noob needs help with new website"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by A_Squirrel on 2007-06-05
Alright,

I registered a domain yesterday and got it working with a webserver running with webmin on ubuntu server. 

If you go to [www.adamrturner.com](www.adamrturner.com) you can see my progress, or lack thereof.
I've been scouring the internet for some help as to how to actually replace the default webpage (which is really a directory?) with something simple, like index.html. I'm having a hell of a time figuring all this stuff out and would greatly appreciate any links and/or information I can get about just setting up a basic website. I actually spend a fair amount of time programming as a hobby, but I'm completely new to linux/ubuntu/apache/webmin, so all of this has been a huge learning curve, yesterday I probably speant about 10 hours getting as far as I did.

Someone please help! Is there a basic directory where I can just drop an html file in?

---

### Post by phr0ze on 2007-06-05
Generally if you stick an index.html file in the directory thats being served, the index page will be shown instead.

---

### Post by LaRoza on 2007-06-05
By default, Apache will serve the file with a .htm or .php or some other extension. Sometimes, .html is not set in the server.

The default page is this, when you type in a URI, such as [http://ubuntuforums.org/](http://ubuntuforums.org/), you are actually just referencing a folder that is specified in the server configuration, if a file has the name index.htm or index.php among others, the server automatically serves that page.

Here is the part of the config file in my apache server, 
```

<IfModule dir_module>
    DirectoryIndex index.php index.php4 index.php3 index.cgi index.pl index.html index.htm index.shtml index.phtml
</IfModule>
```

---

### Post by Chayak on 2007-06-05
[https://help.ubuntu.com/7.04/server/C/httpd.html]("https://help.ubuntu.com/7.04/server/C/httpd.html")  Read this

---

### Post by A_Squirrel on 2007-06-05
Thanks for the link it was really helpful. I figured out that I just needed to drop my index.html into the /var/www file since it was the default directory for the virtual host which I'm guessing takes precedence over the default host. (This is a huge learning curve for me, so I'm making a lot of conjectures.)

The problem I'm having now is that I'm getting a 403 error when I try my site: [http://www.adamrturner.com](http://www.adamrturner.com)
It says I don't have permission, so does it have anything to do with certificates? Do I need a certificate for my site to be viewable or is there a way to change permission for index.html to be viewed?

Edit*
I FIGURED IT OUT! I'M GOING FRIGGIN NUTS! HURRAY! 
Okay, I just had to change permission on the file so that others could read it.

---

### Post by freebeer on 2007-06-05
Nope.. it's not certificates (and you don't need 'em unless you want them for a particular reason.  My guess is that it's a permission error... what is the permission on the file?  I have read permission for everyone.

---

