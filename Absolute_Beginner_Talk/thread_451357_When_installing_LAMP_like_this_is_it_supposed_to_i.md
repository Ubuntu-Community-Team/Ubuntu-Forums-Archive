---
title: "When installing LAMP like this is it supposed to install 2 Apache folders?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-05-22
When installing LAMP like this on Ubuntu Desktop is it supposed to install 2 Apache folders in /etc?
```
sudo aptitude install php5 apache2 mysql-server
```

Previously I had experimented with XAMPP but I didn't like it so I uninstalled it like their webpage described:
```
rm -rf /opt/lampp
```

Now when I'm configuring the LAMP setup I'm confused by the existence of 2 Apache folders named:
* apache
* apache2


*The first apache folder seem to have stored the configurations I made from my XAMPP time.

*The second apache folder don't even have the regular **httpd.conf** file it says it's not neccessary it's just a short describing text file.  Saying it's there for backwards compatability.  The Ubuntu guide says to use this file to configure Apache:
**/etc/apache2/apache2.conf**

So is my first apache folder leftovers from my XAMPP time or does it come together with my Aptitude LAMP install?
I'm confused is things like they should be or haven't I cleaned the XAMPP setup well enough?

---

### Post by Cypher on 2007-05-22
Your installation of "apache2" created the /etc/apache2 directory and XAMPP created the /etc/apache direcotry. When you removed XAMPP, it probably left it's configuration files behind. You can do 'dpkg --purge xampp' or whatever the exact xampp pakage name was and it will get rid of it's files..

---

### Post by apjone on 2007-05-22
This is because XAMPP probably installed apache. Where as you have installed apache2. 
Apache2 is the latest stable release and should be used.  You SHOULD be safe to ```
sudo apt-get remove apache
``` but take a backup of any data before hand as I am unsure about your configuration.

---

### Post by jingo811 on 2007-05-22
I'll try one or the other solution when I get back home tonight.
Could you explain to me when you should use one uninstall solution over the other?
You mentioned:

* dpkg --purge xampp
* sudo apt-get remove apache

I used this method to install XAMPP: **tar xvfz xampp-linux-1.6.1.tar.gz -C /opt**
When is the right time to use "dpkg --purge" or "apt-get remove"?


Another question in WAMP you configure Apache 2.2 with the **httpd.conf** file.
Things seems to be different when I work in Ubuntu, Apache 2.2 no longer seems to be using **httpd.conf** is this normal or do I have to re-create this file so it resembles like how it is in Windows XP?

---

### Post by jingo811 on 2007-05-23
Tried both your methods it didn't bite the **apache folder** is still there now what?  Are you sure that these 2 folders don't come together?
* apache
* apache2

```
mike@sanka:/etc$ **sudo dpkg --purge xampp**
dpkg - warning: ignoring request to remove xampp which isn't installed.
```

```
mike@sanka:/etc$ **sudo dpkg --purge xampp-linux-1.6.1.tar.gz**
dpkg - warning: ignoring request to remove xampp-linux-1.6.1.tar.gz which isn't installed.
```
```

mike@sanka:~$ **sudo apt-get remove apache**
Password:
Reading package lists... Done
Building dependency tree... Done
Package apache is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by az on 2007-05-23
> **jingo811 said:**
> When installing LAMP like this on Ubuntu Desktop is it supposed to install 2 Apache folders in /etc?
```
sudo aptitude install php5 apache2 mysql-server
```


Where did you learn to do that?  It's wrong.

To install LAMP, you need the following packages:
apache2 php5-mysql libapache2-mod-php5 mysql-server

In Edgy and Feisty, you can use the task selector in Synaptic or by running tasksel.

---

### Post by jingo811 on 2007-05-23
> Where did you learn to do that? It's wrong.

To install LAMP, you need the following packages:
apache2 php5-mysql libapache2-mod-php5 mysql-server

Eh I picked it up when I searched for LAMP on ubuntuforums :D  I've been spreading that command to a bunch of newbies also to make things worse.  hehehe *snort* *giggle*

So can I use your CLI text and install it with Terminal like so?
Or how do I install like you do on my Dapper 6.06?
```
**sudo aptitude install** apache2 php5-mysql libapache2-mod-php5 mysql-server
```

---

