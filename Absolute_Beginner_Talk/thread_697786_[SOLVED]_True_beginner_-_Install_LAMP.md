---
title: "[SOLVED] True beginner - Install LAMP"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by snteran on 2008-02-15
I am new to linux and Ubuntu.  I have found some good post on basic installation but they don't seem to be helping me get to my goal of installing LAMP.  I have looked in the Synaptic Package Manager but I do not see any LAMP install.  I then thought I would try to first install apache then mysql and then php, but when I follow the instructions for that, I get an error Couldn't find package apache2.
I am very new to Linux, it took me some time to find the terminal window.  I am a true windows user who is looking to learn some linux to hopefully install Nagios to help monitor our network.  We have no budget for additional tools, so I'm doing my best to learn new methods.  Any help would be greatly appreciated.

Cheers

---

### Post by gandaran on 2008-02-15
maybe this is what you looking for, it's easy to install.
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by FuturePilot on 2008-02-15
Go System&#8594;Administration&#8594;Software Sources. Check all the boxes in the first tab and uncheck the CD-ROM if it's checked. Go to the Updates tab and check the first two boxes and optionally the fourth. Click Close then Reload when prompted. Then try installing again.

---

### Post by kwacka on 2008-02-15
Pretty detailed instructions can be found at [http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)

N.B. installing & using are two completely different things.

See also the Ubuntu instructions at the nagios page at sourceforge.

---

### Post by snteran on 2008-02-26
Well, I have made little progress.  I installed apache but I don't think it's installed correctly.  Typically you go to localhost and you get the apache page.  However I have to go to localhost/apache2-default for a page to come up that says "It works".  So I figure I would try to complete the Nagios install using the instructions from their website.  I follow them step by step and now I get an error: Whoops! Error: could not read configuration data.  I have looked for some solutions, but they don't say much.  Basically that nagios is not started and I need to start.  Well, I'm a true blue windows user and even if it is really easy to do, I just don't know Linux at all.  I have even got a book "Ubuntu Linux - Bible" and I don't seem to be getting anywhere.  I did try the grep and received - 30531 11936 0 15:16 pts/0 00:00:00 grep nagios"

Please let me know if more information is needed.

Thanks,

---

### Post by louieb on 2008-02-26
This is how I did it
```
sudo tasksel install lamp-server
```

about taken from [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

you can run ```
man tasksel
``` to see what else can do

---

### Post by chris.a.barker on 2008-02-26
To aid you in the configuration of Apache, if you are not familiar with the new Apache 2 style I would recommend you download and install webmin. This is basically a web interface for doing administrative tasks on your machine. You can download webmin at [http://www.webmin.com/](http://www.webmin.com/) then click on Debian package.

To install: 
1. ```
sudo apt-get install perl5 libnet-ssleay-perl
```
2. Now click on the file you downloaded from webmin.com
3. Simply use all of the defaults and remember to setup an admin username and password.
4. When this is all finished navigate to [http://localhost:10000](http://localhost:10000) and you should be good.
5. Login with the credentials you setup during the install process.
6. Click on the "servers" tab.
7. Now look for Apache Webserver.
8. Configure your server until your heart's content.

Once you get Apache working as expected you will need to do the following for PHP:

```
sudo apt-get install php5
```

After synaptic is finished installing PHP you can log back into webmin, go to the the servers section, apache, and click on modules. Now ensure that mod_php is enabled. Now just restart the Apache server using webmin and PHP should be good. Once you get this far, post back and we can continue with the mysql portion of this.

---

### Post by snteran on 2008-02-28
Thanks for the help, I'm in the process of updating the system and then I'll try the Ubuntu lamp install.  I need to make sure to install apache correctly.  If this was a windows box, I would know how to edit the file with notepad and then get the apache running from the right location.   But like I always say, 2 + 2 is easy as long as you understand basic addition. :)

---

### Post by MWeather on 2008-02-29
localhost should get you to the parent directory of apache2-default.

Typically, apache uses mod-rewrite to redirect you to apache2-default. 
Ubuntu comments this out of the config file. So your apache sounds like it is working correctly.

As for starting Nagios, assuming you followed the guide for Ubuntu, just type: ```
sudo /etc/init.d/nagios start
```

---

### Post by snteran on 2008-03-05
> This is how I did it
```
sudo tasksel install lamp-server
```

I have started the LAMP install by using the above command.  I started it around 3pm and it has been running all night and it says it's in the process of Configuring MySQL 5.0 and it is at 79%.  How long is it suppose to take to install all parts of the LAMP system?

Thanks,

---

### Post by opositive on 2008-03-05
From what I recall the MySQL installation prompts you at some point to specify a DB admin root password.  It may be that your installation is waiting for a response from you, but it should be prompting you on the same terminal.

---

### Post by steveneddy on 2008-03-05
When I redid my home server, I used the Ubuntu Server 6.06 LTS.

That is a LAMP server out of the box.

Installed from the CD and there was nothing else to do with the exception of loading the web files and pointing to the movies/music/files that I share locally and on the web.

Less than 30 minutes later I have a LAMP system installed and configured.

---

### Post by kwacka on 2008-03-05
Part of the install process involves inserting password & its possibly hung at this process - or a similar - awaiting input from you. 

Is there anything tucked away under the terminal (or elsewhere) waiting for you?

---

### Post by lswest on 2008-03-05
what may have happened is that it timed out, if this is the case, you'll have to either re-install or reconfigure mysql (not sure, i'm just thinking out loud here)

---

### Post by snteran on 2008-03-05
I was prompted for a root password for mysql and I did enter that already.  I did check to see if there was another box tucked away but there was nothing else that I could see.  It does seem like it is stuck.  Is there a place that can show a status of the installation, something like a Task Manager?

---

### Post by snteran on 2008-03-05
I think I will start all over with the command that is in the ApacheMySQLPHP guide.

To remove the LAMP stack remove the following packages:
```

apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1
 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 
mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
 
```

To also remove the debconf data, use the purge option when removing. To get rid of any configurations you may have made to apache, manually remove the /etc/apache2 directory once the packages have been removed.

My question is, do you put in the whole link as it appears above or are you suppose to do certain sections at a time?

Thank you for all your help, I'm not sure I'm learning much, but this is a good first step.  I guess I have worked with Windows so much, I'm not sure how command line installation and removal works.

---

### Post by snteran on 2008-03-05
Dude, OK so I now have apache back to where I had it and I believe I have installed PHP successfully.  I am trying to run my phpinfo() page but I can not add a php file to my var/www folder.  I know this is probably a very easy thing to do, but I guess I just can't figure it out.  I don't have the permissions.  Moving from windows to Linux is not easy.  Can someone please help me out with this.  I can't believe how hard it is to add a file to a folder.  Sorry, but I am a bit frustrated, this has been such a challenge.  I have to install Nagios after all this process.

---

### Post by snteran on 2008-03-07
I wanted to thank everyone for their help.  I now have LAMP installed and it is working fine.  I'm now moving to Nagios and will be following the help guide.  I'll create a new topic if and when I run into any major issues.  
Also, I did find a posting on how to put a file in a certain location.  "Sudo cp filename location", not the most efficient method but it works for now.

Thanks again.

---

