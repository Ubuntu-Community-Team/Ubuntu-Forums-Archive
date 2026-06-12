---
title: "Ampache The Easy Way"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by cjssmo on 2007-09-08
This is generally for new Ubuntu users who would like to have a streaming music server.  There are already several howto guides on how to setup ampache but they do not take into accont the new Debian/Ubuntu Ampache package which greatly simplifies the installation of Ampache.  Some of the howto guides available on this forum suggest that you place Amapache in /var/www.  This is not a good practice to be in as it could possible leave your server vulnerable to attack.  The new Ampache package is lintian and linda clean which means that the package conforms to Debian packaging policy which means that Ampache is installed into the correct location, symbolic links are created correctly, documentation is placed into the correct location etc, etc.  So let's get started

Add one of these lines to your /etc/apt/sources.list.  There are plenty of guides on how to edit your sources.list so it will not be covered here.

For Hardy
deb [http://ppa.launchpad.net/cjsmo/ubuntu](http://ppa.launchpad.net/cjsmo/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/cjsmo/ubuntu](http://ppa.launchpad.net/cjsmo/ubuntu) hardy main

For Gutsy
deb [http://ppa.launchpad.net/cjsmo/ubuntu](http://ppa.launchpad.net/cjsmo/ubuntu) gutsy main 
deb-src [http://ppa.launchpad.net/cjsmo/ubuntu](http://ppa.launchpad.net/cjsmo/ubuntu) gutsy main

For Feisty 
deb [http://ppa.launchpad.net/cjsmo/ubuntu](http://ppa.launchpad.net/cjsmo/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/cjsmo/ubuntu](http://ppa.launchpad.net/cjsmo/ubuntu) feisty main

sudo apt-get update
sudo apt-get install ampache

IMPORTANT:

Ampache **REQUIRES** MySQL server to operate.  MySQL server is not installed 
with Ampache due to the fact that if users are using an older version of 
MySQL server upgrading to mysql-server-5.0 may render their databases corrupt
and possible useless.  So please upgrade your mysql server with **CAUTION**.
For those who do not have mysql-server-5.0 installed it is very easy to install.
In the command line type:

                      apt-get update
	Debian:  apt-get install mysql-server-5.0 (as root)
	Ubuntu:  sudo apt-get install mysql-server-5.0

WARNING

Please insure that older versions of Apache-1.x or later are removed, before
installing ampache or you will experience installation problems.

GETTING STARTED WITH AMPACHE

SUMMARY
	1.  MySQL Server install
	2.  Phpmyadmin or command line setup a MySQL server account with root
	    privileges
	3.  Step 1 Web Interface
	4.  Step 2 Web Interface
	5.  Step 3 Web Interface
	6.  Sign in and start building music catalogs

1.  To install mysql-server-5.0 follow instruction above.  If you already have
mysql-server installed go to step 2.

2.  To setup Ampache you must have a user account on the mysql-server with root 
privileges.  You may do this by either the command line or phpmyadmin.  I prefer
phpmyadmin and that is what will be explained here.  To install phpmyadmin type
in the command line:

	Debian: apt-get install phpmyadmin (as root)
	Ubuntu: sudo apt-get install phpmyadmin

To setup your mysql root account, sign into phpmyadmin by pointing your browser
to [http://localhost/phpmyadmin](http://localhost/phpmyadmin) or [http://your.ip.address/phpmyadmin](http://your.ip.address/phpmyadmin).

username = root
password =

***Leave the password blank this is the default sign in for phpmyadmin.****

This takes you to the main page scroll down to where it says "Privileges" and click
on it.  Now scroll down and click on "Add a new User" and click on it.  Now fill
in

User name = what ever you want
Host      = Any host
Password  = what ever you want
Re-type   = retype your password again

Now Scroll down a little and click on "Check All" for Global privileges.  Now
scroll down to the bottom of the page and click the "Go" button.  Now sign out.

SECURITY WARNING:

After you have Ampache setup and running it would be a very good idea if you
changed mysql root password.  It is widely known the the default sign in for
phpmyadmin is

username = root
password = <blank>

So please change this password, as it is a potential security hole.

3.  Now point your browser to [http://localhost/ampache](http://localhost/ampache) or
[http://what.ever.your.ip.address.com/ampache.This](http://what.ever.your.ip.address.com/ampache.This) will bring you to Ampache's
Web Installation Interface (step 1)

Desired Database Name = ampache
MySQL Hostname  = localhost
MySQL Administrative Username = root or the user name you setup with phpmyadmin
MySQL Administrative Password = leave blank if you use root, or use the password
				you created with phpmyadmin
Create Database User For New Database = set check mark
Ampache Database Username = ampache
Ampache Database User Password = set this to a password you like

Click on Insert Database.

4.  This will take you to Ampache's Web Installation Interface (step 2)

Web Path       = /ampache
Desired Database Name = ampache (default)
MySQL Hostname = localhost (default)
MySQL Username = this is the username you setup with phpmyadmin
				 **root will not work**
MySQL Password = this is the password you setup with phpmyadmin
				 **blank will not work**

Click on Write Config.

Ampache will prompt you to download a file called "ampache.cfg.php".  Download it
to your favorite location.  Now take "ampache.cfg.php and copy/move it to
/etc/ampache.

Now click on check for config, and everything should turn green.  Click on next

5.  This will take you to Ampache's Web Installation Interface (step 3)

Enter a password, you will be using this to initially sign into ampache.  You can
change the admin username and password after the install is complete through Ampaches  
preferences tab

Click next this will take you to Ampache's log in screen.

Enter Admin and the password you entered in the above step.

6.  You are now ready to start adding music and building your music catalogs.

If you have never setup Ampache Catalogs please take a look at this wiki page

[http://trac.ampache.org/wiki/InstallCatalog](http://trac.ampache.org/wiki/InstallCatalog)

---

### Post by iheartme on 2007-09-30
Excellent! Thanks for this, worked like a charm.

---

### Post by cjssmo on 2007-09-30
Thanks, just trying to give back to a community that has given me so much.  

On a side not ampache has been accepted into the Debian repositories.  Ampache should be available through the Ubuntu repositories during the next release cycle (Hardy).  

I forgot to mention but there is also a Themes package for ampache available at the above site, and I am currently trying to get it included into Debian so it will also be available to Ubuntu users.

:guitar:

---

### Post by xxzeenoxx on 2007-10-22
Thanks for the guide, it worked great.  Although, i did run in to one minor snag.  I had my file collection stored on an external NTFS drive, which Ampache did NOT like.  To overcome this issue i had to create a symlink to my files.  To do so, i did the following:


```
ln -s /path/to/real/file /path/to/non-existant/file
```


...hope this helps anyone else who reads this guide.

---

### Post by Mlehliw on 2007-10-25
Wow, thanks. After using gnump3d for so long this is really quite amazing.

And to make this post somewhat useful. For users who have their music on a separate partition like me, you may need to change its umask value in fstab. My fat partition had a umask=007 if you change it to 002, this will give everyone read permissions.

---

### Post by cjssmo on 2007-11-10
Ampache has officially hit the Ubuntu Hardy archives and can be found here

[http://packages.ubuntu.com/hardy/web/ampache](http://packages.ubuntu.com/hardy/web/ampache)

[http://packages.ubuntu.com/hardy/web/ampache-themes](http://packages.ubuntu.com/hardy/web/ampache-themes)

:guitar:

---

### Post by handband2 on 2007-11-27
Project page is here:  [https://launchpad.net/~cjsmo/+archive](https://launchpad.net/~cjsmo/+archive)

Ampache themes can be installed with the following:
```
sudo apt-get install themeampache
```

The Ampache files get installed in the following location:
```
/usr/share/ampache/www
```

---

### Post by cjssmo on 2008-03-21
For bleeding edge ampache users check out the launchpad PPA  

[https://edge.launchpad.net/~cjsmo/+archive](https://edge.launchpad.net/~cjsmo/+archive)

or

[http://tinyurl.com/6yh2hl](http://tinyurl.com/6yh2hl)

It offer the latest greatest ampache packages for ubuntu

---

### Post by NDPeter on 2008-04-02
I keep getting the following message.  It had been showing up when I just installed updates using Synaptic.  I decided to completely uninstall Ampache and am now still getting the same message.

```
Setting up ampache (3.4-r1491-0ubuntu1~gutsyppa) ...
 * Restarting web server apache2                                         [ OK ] 
/var/lib/dpkg/info/ampache.postinst: 55: php: not found
dpkg: error processing ampache (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ampache
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Any ideas where to go from here?  Thanks.

---

### Post by GeneticFlea on 2008-04-06
hey guys, im trying to follow this guide for Gutsy, and ive gotten to step 2, where i need to configure phpmyadmin. I cant use ieither of the links provided to get to the configuration menu. it just gives me a 404 error. what am i doing wrong?

---

### Post by jms830 on 2008-04-28
I think this post would benefit by a quick rundown on how to close the security holes in phpmyadmin. I check privileges and there's several different "root" users, and "Any user." I dont understand it.

---

### Post by kciampi319 on 2008-05-11
Geneticflea I have a similar problem, I can only access phpmyadmin by accessing it externally (not through localhost, or within my network).  I can access mine at [http://externalip:port/phpmyadmin](http://externalip:port/phpmyadmin).  I have a home internet service so port 80 is blocked.  So if you try this you may have to change your /etc/apache2/apache2.conf (if you have apache2) to use a nonstandard port.  This does concern me however I would rather access the server within my network for security reasons.  It probably would not be difficult just to look up how to configure it by commmand line that is how I originally configured mine (I got phpmyadmin just to check it out).

---

### Post by kciampi319 on 2008-05-11
Re: Ampache The Easy Way
Geneticflea I have a similar problem, I can only access phpmyadmin by accessing it externally (not through localhost, or within my network). I can access mine at [http://externalip: port/phpmyadmin](http://externalip: port/phpmyadmin). I have a home internet service so port 80 is blocked. So if you try this you may have to change your /etc/apache2/apache2.conf (if you have apache2) to use a nonstandard port. This does concern me however I would rather access the server within my network for security reasons. It probably would not be difficult just to look up how to configure it by commmand line that is how I originally configured mine (I got phpmyadmin just to check it out).

---

### Post by largess on 2008-05-16
@NDPeter:

I had the same error. I stumbled through the upgrade using the web interface but think the main thing I was missing was this:
    sudo apt-get install php5-cli
I'd do that then try the upgrade from apt-get/synaptic again. Worked for me.

---

### Post by Speff on 2008-06-04
Hm, when I try and install ampache, I keep getting the option to save the file when I try to go to [http://localhost/ampache](http://localhost/ampache)  . I think this is a problem with php , but I don't know what it could be. Can anyone give me any leads?

---

