---
title: "Ubunto server?"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by ClareJonsson on 2006-02-08
Hi folks,

I'm new to Linux and have a little question. I'm presently running a server which hosts my Web and NT domains. I have been meaning to investigate moving from Win 2K Server to Linux for a while, mainly because of security and I'm fed up of having to reboot my server once every two weeks because it's run out of resources.

So I'm guessing, being that Ubuntu is Linux it can be used as a server yes? If this is correct I'm going to give it a try. I am guessing it will be using Apache as the web server, but what about the control of my internal domain. Am I right in thinking I will have to scrap my NT Domain with roaming profiles over my 3 machines and use something else instead?

I am presently downloading Ubuntu 5.10, and will try this on my backup server alongside my W2K server. I guess I am just throwing this question to all you experts so you can point me in the right direction :) .

TTFN,
Clare.

---

### Post by Jedeye on 2006-02-08
this has been one of the best guides I have seen [http://howtoforge.com/perfect_setup_ubuntu_5.10]("http://howtoforge.com/perfect_setup_ubuntu_5.10")

ahh, but im no expert :)

---

### Post by bonzodog on 2006-02-08
Clare, one of the things you can do on install is ask for a server install. This will install a commandline only environment where you can then add whatever server software is needed.

---

### Post by ClareJonsson on 2006-02-08
Thanks guys for the quick replies. I'm going to try Ubuntu over the weekend. I'm also busy learning Flash MXat the moment.

I may have more questions later on next week. Hope I don't become a pest ;)

---

### Post by wrtrdood on 2006-02-08
Ubuntu works quite well as a server-only system.  I'm hosting a website with it and once I got everything set up, "it just works".  The HOWTO mentioned is a good guide for getting what you need in place.  Yes, Apache is the standard webserver and often MySQL is used as the DB backend.  PHP is also common but the latter two are not "required" if you're running a simple intranet webserver.  Many CMS packages require them though.

Read up on Samba.  It can be configured as a PDC so you'll still be able to keep the domains.


Good luck and welcome to GNU/Linux and Ubuntu!

---

### Post by steve.horsley on 2006-02-08
I suggest that you go for a default install rather than a server install. The server install merely omits installation if any GUI stuff. Unless you are really comfortable with using an 80x25 command-line console, this is likely to make your life more difficult than it needs to be.

---

### Post by ClareJonsson on 2006-02-08
So looks like I will go for the standard install then.

I do need PHP and MySQL, how easy is it to install them and migrate databases from W2K server?

---

### Post by madmetal on 2006-02-08
have a look..  [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by wrtrdood on 2006-02-08
Installing is a piece of cake.  Synaptic (apt-get at the command line) is a good place to start for that.  It's the configuration afterwards that can get involved.  But you probably already know that.  Have a look at [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) for starters.

As for migrating a database; it depends.  Is it a MySQL database or MSSQL?  The former is a breeze.  The latter may be a good bit of work.

---

### Post by ClareJonsson on 2006-02-08
[QUOTE=wrtrdood]Installing is a piece of cake.  Synaptic (apt-get at the command line) is a good place to start for that.  It's the configuration afterwards that can get involved.  But you probably already know that.  Have a look at [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP) for starters.

As for migrating a database; it depends.  Is it a MySQL database or MSSQL?  The former is a breeze.  The latter may be a good bit of work.[/QUOTE]

Thanks for the links guys :)

Regarding the databases, I'm presently running quite a few on my present server and they are all MySQL. I like the way PHP and MySQL bind to each other. I'm hoping that it will all go through quite smoothly!

One thing I just thought about, I may have to do some reorganising of my PCs, regarding my NT domain. I might scrap that altogether as roaming profiles and group policies are becoming less of an issue. Also I'm running Active directory on my present server that not only controls my NT Domain, but is my DNS too. I have heard that Linux (Ubuntu) can easily become a DNS server and after installation it is configured by editing a text file, is this true? The main reason I am asking, is because I host a few domains for people, so control of DNS resolution is a must. 

Again, I do apologise for all the questions, sorry to be a pain.

Clare.

P.S. I had another thought. Does Ubuntu have a version of Terminal Services. i.e. Remote Desktop?

---

### Post by David Corrales on 2006-02-08
Hi Clare, welcome to the Ubuntu community :mrgreen: 

**Samba**
First of all, as others already stated, you can use Samba to replicate the domain controller functionality provided by Windows 2000. Samba can work as any of the following:
[LIST]
[*]Regular file sharing client through workgroups
[*]WinNT style primary or backup domain controller
[*]WinNT domain client
[*]Active Directory client
[/LIST]
Support for working as an Active Directory controller is still on the works. So yes, you can keep the roaming profiles, domain logons and all that when you do the switch.

**PHP**
PHP is really easy to install. Just type **sudo apt-get install php**. Or do it through Synaptic. Both are dead easy.

**Databases**
You can choose between MySql or Postgre since both are pretty much integrated into PHP and they now support stored procedures, triggers, etc. Same installation as PHP. Once again, this is very easy.

**DNS**
Of course you can run a DNS using linux. There's the defacto option called *BIND* which supports everything you need for a heavyweight DNS server.
If you're looking for a small zone DNS and don't need all the bells and whistles (plus the complexity) that BIND carries, you can look at other more "lightweight" DNS servers that could perfectly (and in an easier way) fit your requirements.
[http://cr.yp.to/djbdns/other.html]("http://cr.yp.to/djbdns/other.html")
Some more info about other DNS software at that link :)

**Remote Desktop**
I'm pretty sure you can connect to a Windows remote desktop from linux but if you can't, there's the VNC viewer which does the same thing but it's cross platform. You can also forward the remote X desktop to another linux machine if you need to.
Of course you can tunnel all of these methods through SSH to keep things secure :)

---

### Post by ClareJonsson on 2006-02-09
[QUOTE=David Corrales]Hi Clare, welcome to the Ubuntu community :mrgreen: 

**Samba**
First of all, as others already stated, you can use Samba to replicate the domain controller functionality provided by Windows 2000. Samba can work as any of the following:
[LIST]
[*]Regular file sharing client through workgroups
[*]WinNT style primary or backup domain controller
[*]WinNT domain client
[*]Active Directory client
[/LIST]
Support for working as an Active Directory controller is still on the works. So yes, you can keep the roaming profiles, domain logons and all that when you do the switch.

**PHP**
PHP is really easy to install. Just type **sudo apt-get install php**. Or do it through Synaptic. Both are dead easy.

**Databases**
You can choose between MySql or Postgre since both are pretty much integrated into PHP and they now support stored procedures, triggers, etc. Same installation as PHP. Once again, this is very easy.

**DNS**
Of course you can run a DNS using linux. There's the defacto option called *BIND* which supports everything you need for a heavyweight DNS server.
If you're looking for a small zone DNS and don't need all the bells and whistles (plus the complexity) that BIND carries, you can look at other more "lightweight" DNS servers that could perfectly (and in an easier way) fit your requirements.
[http://cr.yp.to/djbdns/other.html]("http://cr.yp.to/djbdns/other.html")
Some more info about other DNS software at that link :)

**Remote Desktop**
I'm pretty sure you can connect to a Windows remote desktop from linux but if you can't, there's the VNC viewer which does the same thing but it's cross platform. You can also forward the remote X desktop to another linux machine if you need to.
Of course you can tunnel all of these methods through SSH to keep things secure :)[/QUOTE]

This is sounding better by the second. Able to use internal domains, Active directory and remote desktops and DNS. Is there anything Ubunto can't do :)

So I should be able to connect to Ubunto from a windows machine in a graphical environment like X (I'm going to have to find some X term software) or a web interface?

Okay now another side to all this, backups. Here is what I presently do. Server 1 incrementally backs up once an hour up to 2 external USB Hard Drives. Only one is connected at a time, the other is off-site and I rotate them weekly. My 2nd server is booted with the removable server HDD installed once a week that uses a batch file to copy all the relevant data from server 1 to itself. In effect I always have an up to date backup on an external drive and the 2nd server is updated once a week. I'm guessing I can use batch files or something in Ubuntu to replicate the above, or is there another super smart way that will accomplish the same? 

Clare.

---

### Post by Iowan on 2006-02-09
I'm sure someone far more experienced than I can/will explain **cron** (or it's latest variant) and suggest a program to do your backups... but it'd be a safe bet to say it's already being done on a regular basis elsewhere.

BTW... not to even SUGGEST you go elsewhere, but you're aware that there's a forum for servers? [http://ubuntuforums.org/forumdisplay.php?f=45]("http://ubuntuforums.org/forumdisplay.php?f=45")

---

### Post by David Corrales on 2006-02-09
Yeah Clare, you can use VNC to access the graphical environment in linux from a windows box.
[http://www.realvnc.com/](http://www.realvnc.com/)
That's the "vainilla" version of the protocol, server/client tools. There's other versions around that use different compressions schemes and so on.

About the backups, like Iowan suggested, you can use **cron** to handle the repetitive tasks.
What **cron** does basicaly is keep a list of all the tasks you need done, with their respective time, commands, repetitions, etc.
For example, you can tell it to:
Run my backup on X day, at Y hour. The backup command can be a full script if you wish and of course there's GUI tools to help you manipulate the **cron** configuration files.

---

### Post by ClareJonsson on 2006-02-21
Okeydoke I got Ubuntu running on my 2nd server, I now need Apache, PHP and MySQL installing, so how do I go about doing this, and in what order should I install them all?

Edit: Ignore that, previously in this thread I found [https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

I will give it a go soon.

Another question, I presently use Winmail Email Server, which has a web interface and IMAP. Winmail is very configurable with filtering and multiple domains etc. What can I use to replace this service?

---

### Post by ClareJonsson on 2006-02-25
Okay I now have Apache, PHP and MySQL running, I think. 

Next problem, how can I gain access to some directories and files as I am obviously not logged on as root. i.e. how can I create or copy files into the www folder? How can I edit the smb.conf file so I can try and set up a samba share to my XP machine?

Clare.

---

### Post by QwizzTest on 2006-02-26
[QUOTE=ClareJonsson]Okay I now have Apache, PHP and MySQL running, I think. 

Next problem, how can I gain access to some directories and files as I am obviously not logged on as root. i.e. how can I create or copy files into the www folder? How can I edit the smb.conf file so I can try and set up a samba share to my XP machine?

Clare.[/QUOTE]
Use *sudo cp 'source_file' .../www/'destination_file'/* for copying the files.  Enter your user password when prompted.  *sudo vi .../smb.conf* should work for editting.  


Where you see '...' insert the location of your files.  

I don't haven't used it yet but there is a samba/ldap installer script here in post #1: [http://www.ubuntuforums.org/showthread.php?t=99417&highlight=samba+ldap+installer](http://www.ubuntuforums.org/showthread.php?t=99417&highlight=samba+ldap+installer)

---

### Post by curtis on 2006-02-26
[QUOTE=QwizzTest]Use *sudo cp 'source_file' .../www/'destination_file'/* for copying the files.  Enter your user password when prompted.  *sudo vi .../smb.conf* should work for editting.  


Where you see '...' insert the location of your files.  

I don't haven't used it yet but there is a samba/ldap installer script here in post #1: [http://www.ubuntuforums.org/showthread.php?t=99417&highlight=samba+ldap+installer](http://www.ubuntuforums.org/showthread.php?t=99417&highlight=samba+ldap+installer)[/QUOTE]


Another option is to use sudo -s, as then you keep root priveleges until you exit.

---

### Post by QwizzTest on 2006-02-26
[QUOTE=curtis]Another option is to use sudo -s, as then you keep root priveleges until you exit.[/QUOTE]
sudo -s.  Thank's curtis!  I learn something everytime I post!

---

### Post by ClareJonsson on 2006-02-28
Okey doke, so how far have I got?
Apache running.
MySQL running.
PHP running.
FTP running.
SSH running.
Remote Desktop Running (Will be dissabled later on).
Samba running.

My next step is to setup a DNS service on Ubuntu. It may already be running but I have no idea if it is or not, how to test or even how to configure it. I manage multiple web domains some have sub domains too. Once I have setup the DNS, I then need to know how to set up Apache for the different web sites that the DNS points the traffic to. Did that make sense?

Anyone feeling like helping or pointing me at a quick tutorial? So far the help I have had here has been fantastic. I didn't think I would have gotten this far at all. 

Thanks guys :roll:

---

