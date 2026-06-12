---
title: "Apache Web Server adding cgi-bin"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by Siggy75 on 2007-10-06
I had Ubuntu Server 7.04 with LAMP stack installed on a new box and all appears fine, esp. to use as an (internal) web server because I can browse to the Apache2-default directory and I get an "It Works" message in the browser. This machine is to be deployed as an internal web server to set-up and use a Help-desk program. I have a "tester" program with cgi script that came from the authors of the Help-desk program. They say just to locate the program in the cgi-bin directory and run the script using a web browser (the script presumably tests for LAMP components and other stuff to see if it's OK to run  their program). Well, there is no cgi-bin directory, so I created one inside the /var/www directory (I used sudo nautilus to do this). I put their tester program in there and ran the script from within Firefox. Lo and behold, I get a 404 error. I can SEE the directory structure and file DOES exist as shown in Nautilus as /var/www/cgi-bin/tester/db.cgi. So I looked for and found the Apache error log file message which I have copied here:  "[error] [client 192.168.1.11] script not found or unable to stat: /usr/lib/cgi-bin". Two things noticeable with this statement. (1) This is a little bit different message that what the browser had, especially what is "unable to stat". Is that a mis-spelling? Is it supposed to say "unable to start"?, and (2) there is no /usr/lib/cgi-bin directory on the machine (at least not that I can find).  Why is the machine referencing a location that does not appear to exist? I only want the browser to run this little script and as you can tell, I'm not  experienced with setting-up web servers. I "chmod" the cgi-bin, tester and all files within to 777. Thank you for any help.

---

### Post by _trainer on 2007-10-12
Hello, (First post from me :) )

I've just installed Ubuntu for the first time and then the lamp stack.
I've had the exact same problem as you.

What I did was to edit the /apache2/sites-enabled/000-default file.

I changed the script alias from **/usr/lib/cgi-bin/** to **/var/www/cgi-bin/**

...and also the directory line underneath that.

Hope this works for you :)

---

### Post by hacme on 2007-10-12
Follow this link for a great how-to.

[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

### Post by Siggy75 on 2007-10-15
Wow, you folks are the greatest! Thank you very much. I think this is good stuff. Thanks for your time! I hope I can help someone, too.:)

---

