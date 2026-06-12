---
title: "MAJOR Novice question? ubuntu,webmin"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by pdumbelton on 2007-10-15
Thanks for taking the time to read & hopefully help me a newbie...

I have never used Linux before. There, I said it,,, I feel better already.

I have just installed ubuntu 6.06 Lamp server & am trying to get webmin to work to allow me to configure apache, mysql & so on.
I have followed the articles I have found regarding install of webmin but when I run the install it errors. 

dpkg Dependency problems prevent configuratio of webmin
webmin depends on libnet-ssleasy-perl; however package libnet-ssleasy-perl is not installed.

I get the same statement for the following files. libauthem-pam-perl, libio-pty-perl, libmd5-perl.

Do I need to download & install Perl5 first? my ubuntu install document didn't mention needing to do this...
Should I be using a different version of ubuntu?... I do require it to have apache & mysql but should I install differently not chosing the Lamp server option right @ the beginning of the install.
Having lived in the microsoft world for to long command line work is foreign to me... I don't mind learning but if there is a simpler way for me I'd rather go that route..?

Your feed back for a poor ubuntu novice would be greatly appreciated.

---

### Post by uclalinux on 2007-10-15
I have install the LAMP server edition, as well as many other editions, I have found its simpler for me to install a regular  editions and add what I need for a server. Here is a howto  of how to have install ampache, I know you don't want ampache, but setting up the apache and php will be the same. 

Also if you are going to use linux, you will most likely  need to get use to the terminal  it is very efficient  once you learn how to use it. 

Ampache
[https://ampache.bountysource.com/wiki/Ampache_on_Debian](https://ampache.bountysource.com/wiki/Ampache_on_Debian)

---

### Post by pdumbelton on 2007-10-15
Thank you for your help.

much appreciated. I will no doubt have to bone up on my command line knowledge.

I found a fix for my problem here. 
[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

Download ‘webmin-1.310.tar.gz’ (at the time of writing) to some location in your machine ex:- /usr/local/src
wget [http://prdownloads.sourceforge.net/webadmin/webmin-1.310.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.310.tar.gz)
cd /usr/local/src
sudo tar xzvf webmin-1.310.tar.gz
cd webmin-1.310
sudo sh setup.sh
This will start the installation and now it will prompt for several questions answer them as follows
Config file directory [/etc/webmin]:
Leave as default, or change as you wish
Log file directory [/var/webmin]:
Leave as default, or change as you wish
Full path to perl (default /usr/bin/perl):
Leave as default, or change as you wish
Operating system:
Enter ‘6&#8242;
Version:
Enter ‘6&#8242;
Web server port (default 10000):
This is where you can start to make webmin more secure then the standard install you get with apt-get, Synaptic, or RPM. Leave as default or change it to what ever port you want.
Login name (default admin):
It is ‘admin’, so you can leave it as that, or put in any name that you like.
Login password:
By creating the user above and giving it a password, you have now made it so you will not need to log into webmin with root.
Password again:
enter your password again
If you did not install ‘libnet-ssleay-perl’ you will get the following message:
‘The Perl SSLeay library is not installed. SSL not available.’ You can continue with the install, but it would be more secure if you install sslrelay.
Use SSL (y/n):y
Choose yes here
Start Webmin at boot time (y/n):y
select here y
At this point it is going to configure things, install things, and create things…It will then tell you that you can log in to [https://hostipaddress:10000](https://hostipaddress:10000) and to accept the certificate.
Webmin User Password Change
If you want to change root password in webmin use this included Perl script:
sudo /usr/share/webmin/changepass.pl /etc/webmin root
If you want to install any standard modules you can download from here
If you want to install third party modules you can download from here

---

### Post by ruibernardo on 2007-10-15
Another more "Debian" way to install webmin (the way you get a package if you want to remove it later via apt-get) is:

```
sudo aptitude install libnet-ssleay-perl openssl libauthen-pam-perl libio-pty-perl libmd5-perl
wget -c http://prdownloads.sourceforge.net/webadmin/webmin_1.370_all.deb
sudo dpkg -i webmin_1.370_all.deb
```Also you can use the webmin repository to have upgrades later. More info about all this here: [http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

---

### Post by mahalie on 2007-10-30
Thanks epimeteo, your simple directions worked!! How do you mark threads as answered?

---

### Post by alwiap on 2007-10-30
[http://ubuntuforums.org/showthread.php?t=327385&highlight=mark+threads+as+answered](http://ubuntuforums.org/showthread.php?t=327385&highlight=mark+threads+as+answered)

:KS

---

