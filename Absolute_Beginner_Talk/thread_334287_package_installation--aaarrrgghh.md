---
title: "package installation--aaarrrgghh"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-01-08
Hi,

I need help getting out of installation hell.  What began as one error when trying to install PostgreSQL is now turning into a nightmare.  

I can't install (or remove for that matter) a score of packages  from my XUbuntu 6.10 (Edgy Eft).  

I tried to install PostgreSQL along with apache2-mod-auth-pgsql and php-pgsql.  The Apache module installed fine but not PostgreSQL, postgresql-common, postgresql-contrib, and because of it neither did the postgresql php module.  The problem was that there was a post-installation script error in postgresql thus creating a dependency problem for php-pgsql, postgresql-common and postgresql-contrib (needs postgresql to install) leaving it unconfigured.     Postgresql-client and doc installed fine.  

When I tried to remove the broken packages like php-pgsql I get a message the pre-removal script returned an error.  

Meanwhile, this is also causing a whole bunch of other packages to be left unconfigured.  I used Update Manager to get updates, and while they all downloaded they are not configured.  I can't update ClamAV, Thunderbird, Firefox, Samba, etc.  Also, I can't install Flexi or Bison which I need to install postgresql from source--something I thought I try to bypass Synaptic.    

The errors are always the same: 

subprocess post-installation script returned error exit status 9

debconf: Problem setting up the database defined by stanza 3 of /etc/debconf.conf.
driver type not specified (perhaps you need to re-read debconf.conf(5)) at /usr/share/perl5/Debconf/Db.pm line 35, <DEBCONF_CONFIG> chunk 3.


as well as dependency problems due to incorrect installations.  

I'm using Synaptic and apt-get to try and install but so far had no luck.  
One of the things I tried was 

apt-get -f install
apt-get upgrade
apt-get -f install
apt-get upgrade
... etc

apt-get -fyu install
apt-get upgrade
apt-get -fyu install
apt-get upgrade
... etc

I also tried using dselect...no help there.  

Please Help.  Thank you kindly.

---

### Post by teaker1s on 2007-01-08
seeing as you haven't had a better reply I'll try
 ubuntu is debian based and this page explains how to resolve your issue
[http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")

---

### Post by x1a4 on 2007-01-08
> **teaker1s said:**
> seeing as you haven't had a better reply I'll try
 ubuntu is debian based and this page explains how to resolve your issue
[http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106]("http://distrocenter.linux.com/article.pl?sid=05/10/12/1952217&tid=106")

Thank you.  While the link you provided did not solve my problem directly, it did force me to 
look at debconf.conf more closely.  Should have known to do it from the start based on the 
error messages,  ](*,)  but anyway ...

The problem was formatting.  To make things more readable I inserted an empty line in the 
first stanza to have the entry Frontend: dialog more visible.  Once I removed the blank line and 
ran apt-get -f install the joy of everything working was awesome.  8) 

After spending as much time as I have on this, to be able to solve the problem just by deleting a single blank line seems ridiculous.  
Oh well, at least I learned something.

---

### Post by teaker1s on 2007-01-09
great result, edit your first post and tick resolved and save:mrgreen:

---

