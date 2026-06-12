---
title: "server as a desktop?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by mayday56 on 2007-04-27
Ive had alot of trouble since i installed a clean install of 7.04 and wiped out xp....one suggestion is dont use fiesty fawn because its too new...so I was thinking about going to 6.06. could I use the server edition as my home pc?will I still have the available programs that come with the regular desktop edition.one reason why i ask is im trying to get a program called swisscenter going. it needs apache,sql,php...Is it true that in the server edition the lamps package is auto installed and configured?

---

### Post by Cypher on 2007-04-27
I would diagree that you shouldn't Feisty Fawn because it's too new, I use it almost exclusively and have had absolutely no problems with it. I'm also well versed with Linux in general so I can handle most..but anyway..

You can absolutely use the server version as your desktop. You'd want to install either GNOME or KDE to get the same look..
```

sudo apt-get install gnome-desktop

```
OR
```

sudo apt-get install kubuntu

```
will get you all that Server brings you and the desktop to manage it all.

---

### Post by az on 2007-04-27
It sounds to me that you will have a much easier time doint it the other way around.  Install the desktop and then add the LAMP stack on top of that.

You will end up with exactly the same LAMP server, configured in exactly the same way.

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Visit:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
and read how to configure the mysql root password so that you can be on your way to installing a web application on your LAMP server.

---

### Post by mayday56 on 2007-04-27
thanx for the reply cypher...the person who told me that just said that 6.06 was known good and that 7.04 might have bugs that are causing my problems.one of them being getting my nvidia 6200 le video card working properly. I tried envy, no go  and then did a fresh install of 7.04 and used automatix2.i orig thought that fixed it but every once in a while it still boots up at 640x480 with no other resolutions to pick from.....

---

### Post by Cypher on 2007-04-27
I'm using Feisty on my machine with an nVidia 7600GT PCIe card, the default installation worked with no problems. I used Envy and had it "install drivers" and I now notice a nice nVidia logo during each boot and everything works normally..

But, by all means, if 6.06 works for you, go for it..

---

### Post by albdeveloper on 2007-04-27
Quick question since this topic is up. Wont the desktop slow down the server, or the other way around?

---

### Post by NICU on 2007-04-27
It is much faster to install the desktop version then install the server components than it is to install the server edition and then install desktop components.  I have tried both ways and its a difference of a few hours.

---

### Post by az on 2007-04-27
> **albdeveloper said:**
> Quick question since this topic is up. Wont the desktop slow down the server, or the other way around?

Since this will also be a desktop system, this is irrelevant.  You wouldn't want to do this with a production server.

---

### Post by Shiner on 2007-04-28
I'm glad I found this thread, re: installing desktop then LAMP.  I didn't remember that the server install was cmd line only and was looking for a way to install Gnome next.  Methinks I'll just start over and install desktop first then install LAMP when I'm ready for that challenge.

---

### Post by az on 2007-04-28
> **Shiner said:**
> I'm glad I found this thread, re: installing desktop then LAMP.  I didn't remember that the server install was cmd line only and was looking for a way to install Gnome next.  Methinks I'll just start over and install desktop first then install LAMP when I'm ready for that challenge.

Well, if you already installed it the other way, you have the same system.   The only thing you may want to install is the desktop kernel  

sudo apt-get install linux-generic (Edgy/Fiesty)
sudo apt-get install linux-386 (Dapper)

if some of your desktop hardware (mice, funky keyboard) is not working properly.  The server kernel does not support a lot of desktop hardware.

---

### Post by gangalee on 2008-04-16
Shiner-

How did your SwissCenter installation go?
I want to do the same thing, any tips?

---

