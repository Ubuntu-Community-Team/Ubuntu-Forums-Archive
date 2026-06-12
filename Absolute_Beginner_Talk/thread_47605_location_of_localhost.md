---
title: "location of localhost?"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-09
Where does ubuntu link as the localhost directory (web root)? I can't find it in etc/apache2/ or etc/php4...

---

### Post by drummer on 2005-07-09
[QUOTE=gammyhand]Where does ubuntu link as the localhost directory (web root)? I can't find it in etc/apache2/ or etc/php4...[/QUOTE]
 /var/www is the directory that opens when you browse to localhost (also 127.0.0.1) with the apache web server installed. Anything you want available to view via the internet/network should go in there, including php pages that need parsing (they won't work anywhere else, AFAIK).

---

### Post by gammyhand on 2005-07-09
[QUOTE=drummer]/var/www is the directory that opens when you browse to localhost (also 127.0.0.1) with the apache web server installed. Anything you want available to view via the internet/network should go in there, including php pages that need parsing (they won't work anywhere else, AFAIK).[/QUOTE]
 Thanks. I am a professional web developer ASP, PHP, Perl, MySQL etc. I just couldn't find the home directory. On my WIndows install it was /server/apache/http_docs/

Hmm...how do I make the directory writeable? As much as I love linux' inbuilt security it can also be a bit annoying at times. I could chmod it to 777 but I don't really want to do that.

---

### Post by drummer on 2005-07-09
np, sorry for the extended description :P

---

### Post by drummer on 2005-07-09
I did chown on my /var/www to change from root to normal user, but I don't know if that's any more secure than chmod.. a little i guess, as it doesn't allow  _everyone_  write access.

---

### Post by gammyhand on 2005-07-09
[QUOTE=drummer]np, sorry for the extended description :P[/QUOTE]
heh, sorry, didn't mean to sound scathing. I was just making conversation :)

What are the recommended chown properties?

---

### Post by drummer on 2005-07-09
I changed the owner and group of www to the logged in user (admin).```
sudo chown admin:admin /var/www
```I'm no expert, but the group change shouldn't make a difference if left out (ie, leave out " :admin " and only change owner). This would apply to me, as admin is the only user on the server and the one that accesses /var/www (through ftp server), but I don't know if it'd be any different otherwise.. also have a read of "man chown" for detailed info.

---

### Post by gammyhand on 2005-07-09
[QUOTE=drummer]I changed the owner and group of www to the logged in user (admin).```
sudo chown admin:admin /var/www
```I'm no expert, but the group change shouldn't make a difference if left out (ie, leave out " :admin " and only change owner). This would apply to me, as admin is the only user on the server and the one that accesses /var/www (through ftp server), but I don't know if it'd be any different otherwise.. also have a read of "man chown" for detailed info.[/QUOTE]
 Ta :)

---

### Post by ecadre on 2005-07-09
I also use apache to run websites (for testing etc, not for public consumption) on my computer.

It is very useful to have several different sites running on your computer.  You may be designing several different websites, or want to run different test installations.

On my computer I have several different accesses to these test websites, along the lines of:

localhost
site1.loc
site2.loc
site3.loc

Each of these sites has php, mysql etc.

To access site1, I just put site1.loc into my browser.

It is very simple to set this up, but not very obvious.  This is what you do.

First you must add the hosts that you want to use to your hosts file.

Go to /etc in Konqueror and open the hosts file.  You will need to right click on the hosts file and choose Actions > Edit as Root.

In the following example two hosts are to set up.  ie.  site1 and site2.  You can set up as many sites as you like.

You hosts file would read as follows;

####### start ######
127.0.0.1   localhost   localhost.localdomain
127.0.0.2   site1.loc
127.0.0.3   site2.loc


# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
########### end #############

You now need to create directories to place the test sites.

Where you put the test sites is up to you and what best fits in with what you are doing on your computer.  However, they should be directories somewhere in your home directory so that you have all the correct permissions and can find them easily.

Next apache needs to be set up.  Editing the apache conf files is a little more complicated, but still easy.

Go to,  /etc/apache2/sites-available and open the default file (again as root)

Save the file as site1, again in /etc/apache2/sites-available.

Now we will edit the file so that it will point towards your site1 directory and use the site.loc host setting.

Change 127.0.0.1  to  127.0.02 on the first and second lines.

Change line 5 where it says "DocumentRoot /var/www/" so that it points at your site1 directory.  Something on the lines of "/home/yourname/www/site1"

This is all you need to do to get the website going and php working.

You may wish to use different error log files (change the "ErrorLog /var/log/apache2/error.log"  line)  

You may want to use a different directory to put CGI scripts.  In this case change the  "ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/"  line so that the second part where it  says "/usr/lib/cgi-bin/" points instead at where you want the cgi-bin to be.  Change the "<Directory "/usr/lib/cgi-bin">" line as well, so that it points at the same directory.

We've now finished editing the site1 file, so it can be saved and closed.

OK, we're nearly there now  :)

The last thing to do is to create a symbolic link to the site1 file in the "/etc/apache2/sites-enabled" directory.

It's very simple, just do the following.  Start a Konsole (shell/terminal) session and put in the following two commands.

cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/site1  000-site1

You'll have to put your password in after that second command.

Go through the whole procedure for each of the sites that you wish to set up.  Remember that you do not have to use site1, site2 etc. , these are just example names.  Also remember that 127.0.0.2 will relate to site1, 127.0.0.3 to site2, 127.0.04 to site3  etc, etc.  Also remember that any new sites also need to be in the hosts file that we edited right at the beginning.


We now need to restart apache.  At the Konsole command line use the following command to restart apache.

sudo apache2 -k restart

It may ask you for your password again.

Now for the result!!

You need to put an index.htm file in your new site root,  after that, open a browser and put "site1.loc" in the URL line and you should get your new site1 index file showing.

There you are  :)

---

### Post by gammyhand on 2005-07-09
[QUOTE=ecadre]I also use apache to run websites (for testing etc, not for public consumption) on my computer.

It is very useful to have several different sites running on your computer.  You may be designing several different websites, or want to run different test installations.

On my computer I have several different accesses to these test websites, along the lines of:

localhost
site1.loc
site2.loc
site3.loc

Each of these sites has php, mysql etc.

To access site1, I just put site1.loc into my browser.

It is very simple to set this up, but not very obvious.  This is what you do.

First you must add the hosts that you want to use to your hosts file.

Go to /etc in Konqueror and open the hosts file.  You will need to right click on the hosts file and choose Actions > Edit as Root.

In the following example two hosts are to set up.  ie.  site1 and site2.  You can set up as many sites as you like.

You hosts file would read as follows;

####### start ######
127.0.0.1   localhost   localhost.localdomain
127.0.0.2   site1.loc
127.0.0.3   site2.loc


# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
########### end #############

You now need to create directories to place the test sites.

Where you put the test sites is up to you and what best fits in with what you are doing on your computer.  However, they should be directories somewhere in your home directory so that you have all the correct permissions and can find them easily.

Next apache needs to be set up.  Editing the apache conf files is a little more complicated, but still easy.

Go to,  /etc/apache2/sites-available and open the default file (again as root)

Save the file as site1, again in /etc/apache2/sites-available.

Now we will edit the file so that it will point towards your site1 directory and use the site.loc host setting.

Change 127.0.0.1  to  127.0.02 on the first and second lines.

Change line 5 where it says "DocumentRoot /var/www/" so that it points at your site1 directory.  Something on the lines of "/home/yourname/www/site1"

This is all you need to do to get the website going and php working.

You may wish to use different error log files (change the "ErrorLog /var/log/apache2/error.log"  line)  

You may want to use a different directory to put CGI scripts.  In this case change the  "ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/"  line so that the second part where it  says "/usr/lib/cgi-bin/" points instead at where you want the cgi-bin to be.  Change the "<Directory "/usr/lib/cgi-bin">" line as well, so that it points at the same directory.

We've now finished editing the site1 file, so it can be saved and closed.

OK, we're nearly there now  :)

The last thing to do is to create a symbolic link to the site1 file in the "/etc/apache2/sites-enabled" directory.

It's very simple, just do the following.  Start a Konsole (shell/terminal) session and put in the following two commands.

cd /etc/apache2/sites-enabled
sudo ln -s /etc/apache2/sites-available/site1  000-site1

You'll have to put your password in after that second command.

Go through the whole procedure for each of the sites that you wish to set up.  Remember that you do not have to use site1, site2 etc. , these are just example names.  Also remember that 127.0.0.2 will relate to site1, 127.0.0.3 to site2, 127.0.04 to site3  etc, etc.  Also remember that any new sites also need to be in the hosts file that we edited right at the beginning.


We now need to restart apache.  At the Konsole command line use the following command to restart apache.

sudo apache2 -k restart

It may ask you for your password again.

Now for the result!!

You need to put an index.htm file in your new site root,  after that, open a browser and put "site1.loc" in the URL line and you should get your new site1 index file showing.

There you are  :)[/QUOTE]
 Hey, I like that idea. I usually use virtual directories in httpd.conf but your way sounds a lot more flexible. I will give it a go.

We run *nix servers at work for our development and it is much easier to have a *nix solution at home for when I work out of the office. I was running apache2/php5 on XP but I am much happier with php4/apache3/mysql4 at home as we still run php 4 at work (I don't generally think PHP versions become stable enough until at least the third release).

---

### Post by ecadre on 2005-07-10
[QUOTE=gammyhand]Hey, I like that idea. I usually use virtual directories in httpd.conf but your way sounds a lot more flexible. I will give it a go.

We run *nix servers at work for our development and it is much easier to have a *nix solution at home for when I work out of the office. I was running apache2/php5 on XP but I am much happier with php4/apache3/mysql4 at home as we still run php 4 at work (I don't generally think PHP versions become stable enough until at least the third release).[/QUOTE]

One of the things that I found pretty quickly on my move over to Linux was how much easier it was to interact with remote servers (Linux/Apache of course) and develop for them.

The understanding of Apache, PHP etc goes by leaps and bounds because you are essentially working in the same environment.

I have to admit that my own understanding of these things is more practical than particularly deep.

I've found the setup outlined above incredibly useful.

---

