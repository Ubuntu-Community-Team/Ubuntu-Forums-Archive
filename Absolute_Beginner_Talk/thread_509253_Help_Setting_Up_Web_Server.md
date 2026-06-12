---
title: "Help Setting Up Web Server"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by kennyn on 2007-07-25
Hello, I have installed Ubuntu without a problem along with gnome 2.18.1. I am now at the point i want to set up a web server to host my website. I am not sure where to go from here. Any help would be great. I also have the small problem of having an ISP that uses Dynamic IP Address and i have my machine networked through a netgear routher. Any help would be great. If there is a tutorial already set up I would be ablidged if someone can direct me to it. THank you.

---

### Post by kennyn on 2007-07-25
Found part of my own answer. Found this tutorial online. ONe thing i am having problems with i hope someone can help me out. 

The tutorial can be found here:

[http://articles.techrepublic.com.com/5100-1035_11-6180622.html](http://articles.techrepublic.com.com/5100-1035_11-6180622.html)

When I get to FIgure B 

I do not See Open Administrator Settings

Logged in as an admin or as root. Can anyone please explain where Administrator Settings are in the latest version of gnome. Thank you.

---

### Post by reckless2k2 on 2007-07-25
To do an apache setup you can follow the apache area of this tutorial:

[http://www.howtoforge.com/perfect_setup_ubuntu704_p6](http://www.howtoforge.com/perfect_setup_ubuntu704_p6)

You sound like you need a lot more going though. You might want to step back to the beginning of that tutorial on IP and hostname config stuff along with bash relinking. 

As far as DDNS, you'll need to pay for a service for DDNS. I use no-ip. Some people use dyndns. There are a bunch out there. If most of this sounds like a foreign languauge, you'll have to do a little reading into each. Apache setup is not hard at all and if you are writing in simple html you can have something going pretty quick. Resolving a dynamic IP is a DDNS solution. There are free solutions or you can get a domain name with DDNS service like no-ip. no-ip has free service too using their domain names.

---

### Post by kennyn on 2007-07-25
Does anyone have an idea how to do this using the gnome gui front end. I am using the latest version of the gnome gui. Not that I dont want to code it, i am just figuring there has to be a way to do this using the prefrences or something.

---

### Post by punx45 on 2007-07-25
use the software updater/installer (apt GUI frontend) and install apache or apache2 whichever you prefer.

i dont use gnome so i cant give you a click for click instruction, sorry

once you get it installed, all the configuration is done with text files, which you can edit with gedit.  then you can use any guide, and not one specificially written for a specific version of a specific desktop suite.

also, there are some free dynamic DNS providers, but you will have to live with a subdomain of their domain names.   i used to use dyndns.org.

---

