---
title: "Ubuntu Server (Web Server)"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by ev5unleash1 on 2007-09-05
Ok, So here's the deal I'm running a Windows XP server with crappy FTP, web hosting and MySQL software.

I want free software and a one easy to replace. So I was looking into Ubuntu Server as I am using Ubuntu right now. All I am hosting is a phpbb site and a regular website on a certain port (1212) I just wanna know if I can change the port from 80 to 1212 so I can host my site. I also want to know if I can easily manage the server with a graphical interface (no commands on the terminal for turning it on or managing it) i just need to know incase the server has a problem. I'm usally gonna manage it's files from FTP and I already have the site so i'm baslically switching from Windows and want to be able to manage the user accounts statics and stuff like a do now with the Ubuntu server.

I'm downloading it right now and about to install it but I was wondering if it could so all of that?

---

### Post by KCPokes on 2007-09-05
Yes, you can do all of that.  

For your basic webserver install, follow this guide  [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_PHP_for_Apache_HTTP_Server)

For GUI administration, I'd suggest Webmin ([http://www.webmin.com](http://www.webmin.com)).  There is an Apache section that allows you to do a majority of the configuration via a webbrowser.  I do not necessarily recommend the GUI approach as things are easier editing the config files, but then again I prefer CLI.  

Once you have Webmin installed, you can change the default Apache listening port from 80 to 1212.  The one thing I'd recommend is setting up SSH instead of FTP.  This will allow you to use SFTP to transfer files and not leave you with a security hole that FTP opens.  

Good luck.

---

### Post by ev5unleash1 on 2007-09-05
WEll how about manging the server when your right in front of it. Cause I want it to be an ese to manage it from right there is a problem. I still perfer Graphically manging.

---

### Post by KCPokes on 2007-09-05
Apache is essentially a daemon process which was originally not set up to have a graphical frontend.  One much keep in mind that there is a difference in the flavors of linux:  desktop versus server.  To run a server one should really use a server install, which excludes all the graphical interfaces.  Most servers are not in a place to which a administrator can sit down in front of it.

Either way, you'll have to do some searching because I don't know of any good GUI tools for configuring Apache.  Webmin will provide you a graphcial way of administrating all your processes, via a webbrowser.

---

### Post by ev5unleash1 on 2007-09-05
This guy told me of this webmin at webmin.com and it's suppost to manage the Apache server. THey only reason I will HAVE to go to the server if it crashs and I have to for some odd reason go to it and fix it. I really want to have the remote access to mange it though a login on a certain page like I had the feature that used Apache and I could remotely manage it and restart process, change ports, manage users, see stats all of that stuff. But i just really need to manage FTP users and change the port once and see how it's doing and if there is any problems. That's it.

---

### Post by ev5unleash1 on 2007-09-06
Ok, I've just installed the Ubuntu SErver Version 6.10. I'm right in front of it and woudl like to get my server back up and running soon. How do I set up the site and FTP?

---

