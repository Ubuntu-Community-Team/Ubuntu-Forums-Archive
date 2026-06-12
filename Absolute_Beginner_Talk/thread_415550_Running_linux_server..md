---
title: "Running linux server."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by mike-db on 2007-04-20
Ok, I need to setup a linux based server for a school project. I have kubuntu and ubuntu desktop versions on a CD, and I'm not able to brun anymore .sio files because I don't have XP. Could I run a server with ubuntu desktop version? Or would I need the server version.

---

### Post by Winterdream on 2007-04-20
This [LAMP document]("https://help.ubuntu.com/community/ApacheMySQLPHP") might help you.  I was able to follow these instructions (with some help! :)  ) after installing the desktop.

---

### Post by Cypher on 2007-04-20
> **Winterdream said:**
> This [LAMP document]("https://help.ubuntu.com/community/ApacheMySQLPHP") might help you.  I was able to follow these instructions (with some help! :)  ) after installing the desktop.
I'm not sure what LAMP has to do with the OP's question about setting up a Linux Sever.

@OP: You can burn ISO's from within Linux as well, so you are not completely lost without XP. You can burn using the command line "cdrecord" or the multitude of front-ends available like CD-Roast, Gnomebaker and so on. 

Now you COULD set up a server based on the Desktop installation, but you might have to install a few specific packages that are probably not part of the Desktop installation.

Now what purpose would this server serve? In most cases I imagine it's something temporary and the Desktop version will suffice.

Regards

---

### Post by IYY on 2007-04-20
The desktop version is perfectly suited for server use. All server software is available from the repositories (you'd probably want FTP, SSH, HTTP, and so on).

---

### Post by mike-db on 2007-04-20
The server, is for in school use. Me and along with other students are going to be making websites hosted on this server. I'm still not sure if my teacher is going to just make it a network type of server or a online one.

---

### Post by Sef on 2007-04-20
> The server, is for in school use. Me and along with other students are going to be making websites hosted on this server. I'm still not sure if my teacher is going to just make it a network type of server or a online one.

Check out Edubuntu and see if that fits your needs.

---

### Post by mike-db on 2007-04-21
I don't think I would have to go that extreme for a server only one class is going to use. And I'm the one who is going to be maintaining the server not school techs. :P Unless edubuntu is easier for server side things I really want to avoid the download when I already have ubuntu on a disk.

---

### Post by mike-db on 2007-04-30
Alright, I got my hands and two versions of ubuntu server edition. 6.01 and 6.10 Which one should I use? Also how easy is it to start running a web server with it?

---

### Post by Nythain on 2007-04-30
you really didnt have to waste cd's getting server edition in all reallity, desktop woudl have worked fine... i would recomend 6.10 as long as you dont have any funky hardware, edgy seems (according to most) to be the most stable and offer the best hardware support at the moment. if you do decide that you want a gui later, remember that you dont have to start over, you can just install a desktop by typing sudo apt-get install ubuntu-desktop or kubuntu-desktop or xubuntu-desktop etc etc etc as long as you have a working internet connection on it

---

### Post by etank on 2007-04-30
After installing the server apps (ie. MySQL, Apache, etc) the only differences would be that the "server " has a gui interface and it would not be running the server kernel. Everything else should be the same as using the server CD.

---

### Post by mike-db on 2007-04-30
Alright so I went with 6.10 and I'm using [http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10) to setup my server. Can someone help me out here? When I edit "/etc/network/interfaces" I'm not sure how to exit the editor and do "/etc/init.d/networking restart" I'm quite noobish at this. does anyone maybe have a better website that can explain this in full?

---

### Post by mike-db on 2007-04-30
So I found another site that explains a bit more [http://www.unix-tutorials.com/go.php?id=705](http://www.unix-tutorials.com/go.php?id=705)
But I'm still confused. When I'm editing "/etc/network/interfaces" with "sudo vi" command I'm not sure how to exit the editor so that I can enter this command "sudo /etc/init.d/networking restart" Please I'm really in need of help. :P

---

### Post by az on 2007-04-30
> **mike-db said:**
>  Please I'm really in need of help. :P

Start over.  Install the desktop version and in a terminal run

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Once that is finished (it takes three minutes) you need to set up a mysql root password and then you can install your web application onto your server.

What web application are you going to use?

This page is really what you want:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
along with this:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

That other tutorial is overkill and too complicated.

---

### Post by mike-db on 2007-04-30
I'm really not sure what web application I'm going to use. =/ All my teacher said was "make a linux server" only linux I know of that is easy to use and install is ubuntu.

Would it not be easier to install server edition 6.01 because it does have desktop and then from terminal run "apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server" Or would this all just be more easy with a normal desktop version... Because it would be kinda nice to figure out how to use the server edition of things.

---

### Post by az on 2007-04-30
> **mike-db said:**
> I'm really not sure what web application I'm going to use. =/ All my teacher said was "make a linux server" only linux I know of that is easy to use and install is ubuntu.

Would it not be easier to install server edition 6.01 because it does have desktop and then from terminal run "apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server" Or would this all just be more easy with a normal desktop version... Because it would be kinda nice to figure out how to use the server edition of things.

There is no server "version".  There is a server install disk, which only contains the base system and the server packages (no desktop or any graphical apps, since you won't want to install/use them on a production server).  If you install a desktop system and then install the LAMP stack on top of that, you end up with exactly the same thing, except that you have a desktop.  For your purpose, it would be fine to install the desktop.  It is a faster install (the live cd install happens faster than the text-based install because they work differently)

See this, too:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by mike-db on 2007-04-30
Alrighty I'll do it! :D

---

### Post by mike-db on 2007-04-30
Well there ar ejust a few steps on that page that I don't get...

> 
1- Set up dynamic DNS and port forwarding to your server

2- Install LAMP on your server. Install accessory software like SSH and phpmyadmin

3- Check your dynamic DNS url to see if you can reach your server from the internet

4- Install your web application

5- Configure your web application

6- Secure your server by removing unneccesary permissions and reading appropriate documentation. 

Just those ones...

---

### Post by az on 2007-05-01
> **mike-db said:**
> Well there ar ejust a few steps on that page that I don't get...


Just those ones...

1.  If you have a residential internet connection, you need dyndns because your IP address keeps changing.  If you have a static IP address at school, this does not apply to you.
2.  sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
If you want to log in to the server from somewhere other than right in front of it, install ssh.  If you want to configure your database from a web page, install phpmyadmin (that package is in the universe repo)
3.  May not apply to you.
4.[https://help.ubuntu.com/community/Servers#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4](https://help.ubuntu.com/community/Servers#head-ed0a847767fb61cd99eed5e6b641c2ccf11cdea4)
What website software do you want to run?
a forum? [https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)
a more general site? [https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)
6.  In your case, you will just keep it simple.

---

### Post by mike-db on 2007-05-01
Stupafied! Awesome, thanks. If I could I'd kiss you.

---

### Post by mike-db on 2007-05-02
Alright when I do "sudo apt-get install apache2" It says "E: Couldn't find package apache2" soo what should I do in this instance?

---

