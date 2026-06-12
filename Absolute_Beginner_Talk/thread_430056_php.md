---
title: "php"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-05-01
I'm starting to learn php. I've d/l xamp and followed the directions to install it. Now when I type in php snippets into text files ending with .php firefox won't open them and If I try to put the snippets into existing web pages I get a small php icon where the result of the code should be. What gives?

---

### Post by Bachstelze on 2007-05-01
You can't just open PHP files with for example

```
file:///home/user/file.php
```

you must put them in the root of your Apache server (/var/www by default in Ubuntu) and type this in Firefox :

```
http://127.0.0.1/file.php
```

---

### Post by az on 2007-05-01
> **woodsonoversoul said:**
> I'm starting to learn php. I've d/l xamp and followed the directions to install it. Now when I type in php snippets into text files ending with .php firefox won't open them and If I try to put the snippets into existing web pages I get a small php icon where the result of the code should be. What gives?

If you installed the LAMP stack the traditional way, as in using the repos, I could help you.  Actually, it would already work...

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


It takes about three minutes to download and install the lamp stack

---

### Post by bobplano on 2007-05-01
you need to make sure you have the php module ( i think it's called apache2-php5mod or something) then put the files in your index folder. then you click on the file and it should render correctly. name it index.php if you want it to show up by just going to the site. you might need to change httpd for that to happen though

---

### Post by woodsonoversoul on 2007-05-01
> **az said:**
> If you installed the LAMP stack the traditional way, as in using the repos, I could help you.  Actually, it would already work...

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


It takes about three minutes to download and install the lamp stack

I installed everything through synaptic package manager until I got to mysql-server. when I tried to install that I got this error message

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

---

### Post by woodsonoversoul on 2007-05-01
> **HymnToLife said:**
> You can't just open PHP files with for example

```
file:///home/user/file.php
```

you must put them in the root of your Apache server (/var/www by default in Ubuntu) and type this in Firefox :

```
http://127.0.0.1/file.php
```

trying to move the file through the file browser and it's saying I don't have permission. how can I fix this?

---

### Post by bobplano on 2007-05-01
gksudo nautilus or sudo cp file /place/to/copy/to

---

### Post by woodsonoversoul on 2007-05-01
I've moved my file test.php to var/www and when I type [http://127.0.0.1/test.php](http://127.0.0.1/test.php) into firefox's address bar I get a 404 error message

---

### Post by woodsonoversoul on 2007-05-01
Anyone got any ideas?

---

### Post by bobplano on 2007-05-01
so there are no files when you just go to localhost?

---

### Post by woodsonoversoul on 2007-05-01
when I type in [http://localhost](http://localhost) I'm taken to [http://localhost/xampp/](http://localhost/xampp/) I'd love to erase this xampp stuff once I get my LAMP stack installed through the repositories like az was talking about, but I'm running into the error message when trying to install mysql-server where it says it's unable to configure it...

---

### Post by bobplano on 2007-05-01
well localhost basically equals 127.0.0.1 so the file might not be in the right place if you are just going to 127.0.0.1/test.php, because of the redirection

---

### Post by Bachstelze on 2007-05-01
My guess is that your "XAMPP"-thingie sets the root of Apache ton something else, you'll need to find where.

---

### Post by woodsonoversoul on 2007-05-01
Alright, I'm erasing the xampp package and seeing what happens

---

### Post by woodsonoversoul on 2007-05-01
except that it says that I can't remove opt/lampp because it's a directory. even when I use the sudo command

---

### Post by woodsonoversoul on 2007-05-01
thanks for all your help

bump

---

### Post by woodsonoversoul on 2007-05-01
I'm still seeking some solutions for why I can't d/l and configure mysql-sever from the repositories

---

### Post by bobplano on 2007-05-01
```
sudo rm -rf *directiry name*
```
to get rid of directories, but i think you might have to get rid of some more things. you might try going to [http://www.mysql.com](http://www.mysql.com) and getting the .deb

---

### Post by Robynsveil on 2007-05-01
> **woodsonoversoul said:**
> I've moved my file test.php to var/www and when I type [http://127.0.0.1/test.php](http://127.0.0.1/test.php) into firefox's address bar I get a 404 error message
I had a problem getting Apache2 and php working... came to find out I had Apache *and* Apache 2 running as services. Check in your System-> Administration-> Services dialog... disable (untick) and uninstall Apache if Apache2 is running...

---

### Post by woodsonoversoul on 2007-05-01
Alright xampp successfully removed (directory deleted), only apache 2 was running under services, now localhost and home ip gives me a 404, and I still can't repo install/configure mysql-sever I'll try the .deb thing. thanks all

---

### Post by woodsonoversoul on 2007-05-01
which package should I get from mysql.com? (enterprise, etc...)

---

### Post by Robynsveil on 2007-05-01
> **woodsonoversoul said:**
> Alright xampp successfully removed (directory deleted), only apache 2 was running under services, now localhost and home ip gives me a 404, and I still can't repo install/configure mysql-sever I'll try the .deb thing. thanks all
Okay, so it sounds like ph isn't running yet... put a file called phpinfo.php into your /var/www folder with the following code in it:
```
<?php
echo phpinfo();
?>

```

In your browser address bar, put 

> [http://localhost/phpinfo.php](http://localhost/phpinfo.php)

If that gets you an error, you might need to re-install or properly configure php.

---

### Post by Robynsveil on 2007-05-01
> **woodsonoversoul said:**
> which package should I get from mysql.com? (enterprise, etc...)

I would install from this page:
[http://dev.mysql.com/downloads/](http://dev.mysql.com/downloads/)

and choose Community Server - that's the free one...

---

### Post by woodsonoversoul on 2007-05-01
still got a 404. will try to reinstall through repositories

---

### Post by az on 2007-05-02
> **woodsonoversoul said:**
> I installed everything through synaptic package manager until I got to mysql-server. when I tried to install that I got this error message

E: mysql-server-5.0: subprocess post-installation script returned error exit status 1
E: mysql-server: dependency problems - leaving unconfigured

If another instance of mysql server is running, it won't be able to start.

You removed Xammp, so try fixing the half-installed package:

sudo apt-get -f install

and post the complete message, not just two lines if you get an error.  It's helpful to see what packages you installed at the same time and so forth...

---

### Post by woodsonoversoul on 2007-05-02
Thanks az. The message I get after entering that reads:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtk1.2 libwxgtk2.4-1 libwavpack0 libgtk1.2-common python-wxgtk2.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by woodsonoversoul on 2007-05-02
bump

---

### Post by woodsonoversoul on 2007-05-02
I'm trying to keep this from falling off the front page. Can anyone see the problem from the output I posted?

Robynsveil - I got the community server, (mysql-5.0.37-linux-i686-glibc23) where should I extract it to, and how would I set it up?

---

### Post by woodsonoversoul on 2007-05-02
I'm off to work but bump for any possible responses. Thanks again...

---

### Post by bobplano on 2007-05-02
well if your using dapper then you can just get the package. it seems your not though. what you do when you get a tar.gz (or bz2) you extract it anywhere and then generally you  can just run
```
sudo make
sudo make install
```
if this gives you errors like stdio.h is missing or something then run this
```
sudo apt-get install cpp gcc build-essential linux-headers-$(uname -r)
```
then run the make commands

---

### Post by az on 2007-05-03
Why is mysql not starting?


run:

sudo /etc/init.d/mysql restart

and post the output.

---

### Post by adza on 2007-05-03
create a file with the following line...


*** oops, this has been covered in earlier posts***** 


<?php phpinfo(); ?>

save that as phpinfo.php (or whatever.php) into your /var/www/ directory

then browse to 127.0.1.1 (or whatever your localhost is - found in your apache config)

you should then see a list of tables defining what php options are running on your server..

if not, then php hasn't been correctly installed on your machine..

first place to check is php.ini file... make sure the line 

bind 127.0.0.1 is commented out....

---

### Post by woodsonoversoul on 2007-05-03
I'm not really familiar with the "make commands", but I'll look them up. Can anyone see a possible problem in the terminal output I posted? Any other ideas?

---

### Post by woodsonoversoul on 2007-05-03
az - 
The output was:
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
not very telling...

(there was a significant pause when trying to start MySQL)

---

### Post by az on 2007-05-03
try removing mysql-common and mysql-server.  Use the purge option to get rid of the debconf configuration settings the package manager would save (if any...),  Then delete /etc/mysql

Try reinstalling those packages again after that.

---

### Post by woodsonoversoul on 2007-05-05
I successfully removed all those packages. How can I copy the details of what the terminal is displaying when I try to re-install them, I'm getting some error messages, this seems useful

---

### Post by woodsonoversoul on 2007-05-05
also, now synaptic seems frozen. Hasen't changed in about 5 minutes...

---

### Post by woodsonoversoul on 2007-05-05
still no change from synaptic. I'm going to close it before it says it's officially done. It's stuck on mysql-server-5.0

---

### Post by woodsonoversoul on 2007-05-05
bump
I'll post this on one of the other boards tonight and see if I get anymore responses...

---

### Post by ticopelp on 2007-05-05
So... just to get current on the situation...

you can't sudo apt-get install mysql-server at all? What happens when you try?

I followed the instructions here: 
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)

Apache and PHP installed fine -- you just have to make sure to replace PHP4 with PHP5 when using apt-get to install PHP. 

Using apt-get to install mysql-server is the only solution that worked for me when trying to get MySQL working, though.

---

### Post by ticopelp on 2007-05-05
Incidentally, the Apache / PHP install didn't work for me until I logged out and back in again. I'm sure there's a way to restart all those services fom the command line, but I don't know what they are off the top of my head..

---

### Post by adza on 2007-05-06
to restart the apache server... type sudo /etc/init.d/apache2 restart

php is configured in the apache server so no need to 'restart' it... also, this holds for all services in ubuntu..

ie, sudo /etc/init.d/mysql restart for example...

---

### Post by ticopelp on 2007-05-06
Thanks very much!

---

### Post by woodsonoversoul on 2007-05-07
J don't have "/etc/mysql/my.cnf" how do I get that/why don't I have it?

---

### Post by cyphur335 on 2007-05-09
Were you able to figure out what was causing you so much trouble?  

I installed Feisty Fawn, and then isntalled the LAMP stack, and it has worked for me ever since.  I am interested as to what is causing you these troubles!

---

