---
title: "How to port forward XAMPP from 80?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-30
I believe my ISP blocks port 80, which XAMPP uses that port.

How do you port forward 80 to something else?  I know how to do that in router settings, but not on XAMPP side.

For instance, VNC has a config file where you set the new port...

Is there a config file for XAMPP?

---

### Post by jamesrfla on 2008-03-30
What is you ISP? There is a way to allow port 80 to get through your modem. After that you port forward port 80 in your router.

---

### Post by louieb on 2008-03-30
You need to find the apache configuration file. Don't know what an XAMPP install calls it. Maybe [FONT=Helvetica, Arial, sans-serif]httpd.conf or apache2.conf.  In a normal Ubuntu LAMP install its a include file named  /etc/apache2/ports.conf.

Should be a line that reads **Listen 80**. Just change the line to whatever port you want to listen to   [/FONT]

---

### Post by BlizzofOZ on 2008-03-30
> **louieb said:**
> You need to find the apache configuration file. Don't know what an XAMPP install calls it. Maybe [FONT=Helvetica, Arial, sans-serif]httpd.conf or apache2.conf.  In a normal Ubuntu LAMP install its a include file named  /etc/apache2/ports.conf.

Should be a line that reads **Listen 80**. Just change the line to whatever port you want to listen to   [/FONT]

That's what I thought... I found /etc/apache2/apache2.conf, in it it points/includes the use of the /etc/apache2/ports.conf file.  I changed the "LISTEN 80" to "LISTEN XXXXX".

XXXXX being my new port.  In my router setup, I added port forward for XXXXXX to my server.

Stopped and restarted XAMPP... and when I view the localhost/username, everything comes up as it should as it did before.  Now, I haven't seen any screen shots, but in my Firefox web browser, what I see is a folder/directory structure.

Under the structure, I see the following:
Apache/2.2.8 (Unix) DAV/2 mod_ssl/2.2.8 OpenSSL/0.9.8e PHP/5.2.5 mod_apreq2-20051231/2.6.0 mod_perl/2.0.2 Perl/v5.10.0 Server at localhost Port 80

Notice the Port 80... this is part of what is throwing me.  Additionally, I can't access this via the internet.  Either using my outside IPaddy/username or hostname/username.

---

### Post by BlizzofOZ on 2008-03-30
Well, I found this post over on Apache Friends forum... I tried it and it seems to work:
[URL="http://www.apachefriends.org/f/viewtopic.php?t=27138&highlight=port+8000"[/URL]

Now, I have tried this within my network, using my hostname:port/username.  I want to have my friend try this, which will be accessing from outside the network.

It this works... great!  

What can I do to make this more secure???

---

