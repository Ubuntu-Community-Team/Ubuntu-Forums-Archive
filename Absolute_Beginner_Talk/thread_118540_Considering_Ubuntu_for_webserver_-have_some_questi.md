---
title: "Considering Ubuntu for webserver -have some questions"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by jimwillsher on 2006-01-17
Hi all,

My first post here, so please be nice :-) I'm very much a Linux newbie, having got this far more by luck than skill. When things go wrong I spend days with google.....

Some background:

I currently use CentOs 4.2 for my webserver, with:

3Ware SATA RAID controller
2Gb memory, P4

sendmail
apache
php
mysql
procmail
dovecot
vsftpd
spamassassin
squirrelmail

The webserver is live, serving 6 websites, and my server is my email point. I use webmail (squirrelmail) extensively. I don't mind using proftp instead of vsftp. I'd probably like to use PHP5 and MySql5. Happy with Apache 2, but willing to try 2.2. if it's stable.

I also use the slimserver ([www.slimdevices.com](www.slimdevices.com)) music player, and it seems to work best with perl 5.8.7. I only have 5.8.5, and upgrading seems a nightmare, so I'm considering a full blown migration to Ubuntu.


Anyway, my questions:

1) If I install Ubuntu in server mode, what is the general procedure for then installing the above modules/applications? All the Ubuntu documentation seems to refer to Synaptic, which is GUI. I'll be running purely in server mode.

2) Does anybody here run a similar setup to me, and if so could they give me their war-stories (or confidence!).

3) My normal uptime with CentOs is > 150 days. Is Ubuntu capable of matching that? I'm concered that it seems to portray itself as a Desktop distro.

Once my server is set up, I generally leave it alone. I'm not a tweaker, if things work then I'm happy.

All advice very welcome.

Many thanks for your time.



Jim Willsher
Central Scotland

---

### Post by lutrafobic on 2006-01-17
1. Ubuntu is debian-based witch means that you have the wunderful apt-get to install/remove software. You can also use aptitude if you like, it's based on apt too. ("Synaptic Package Manager" is just a GUI for apt-get)

e.g.  ```
 sudo aptitude search apache2 
```
will give you the search result for the word "apache2"

e.g. ```
 sudo aptitude install apache2 
```
will install the "apache2" package.


3. My ubuntu 5.04 has been up for over 200 days and is not giving me a reason that it's going down :-D

---

### Post by nvez on 2006-01-17
[QUOTE=jimwillsher]1) If I install Ubuntu in server mode, what is the general procedure for then installing the above modules/applications? All the Ubuntu documentation seems to refer to Synaptic, which is GUI. I'll be running purely in server mode.
[/QUOTE]

If it says to search for some package, "apt-cache search apache2" - and you can use wildcard in that. (obviously replace apache2 with the package you want to check for).  If it exists then you can install by using "apt-get install apache2" (replace again..) -- apt-get is like Synaptic terminal side. (make sure you edit your /etc/apt/sources.list -- there are a lot of threads about good reporesries(sp?))


[QUOTE=jimwillsher]2) Does anybody here run a similar setup to me, and if so could they give me their war-stories (or confidence!).[/QUOTE]

I had set it up as a webserver before with Ubuntu, running with plesk.  Was rather easy. (thanks to apt-get)

[QUOTE=jimwillsher]3) My normal uptime with CentOs is > 150 days. Is Ubuntu capable of matching that? I'm concered that it seems to portray itself as a Desktop distro.[/QUOTE]

Yep, my linux+plesk server had over 172 days but then I didn't need the server anymore.

---

### Post by jimwillsher on 2006-01-17
Brilliant, many thanks to both of you. it sounds very promising!

I have a test server at my disposal (an old brick!) but it will suffice for a test-install. I'll try it out this evening and see what happens.

Thanks again, much appreciated!



Jim

---

### Post by tgalati4 on 2007-04-08
Depending on your hardware (CPU (PII or better), RAM 256 MB or better) the gnome desktop doesn't add that much overhead.  I recently had to upgrade a Dapper Drake machine after 165 days of uptime.  I had about 100 patches to install.  The gui does make things easier to maintain, especially if you haven't touched the machine in half a year.

There are lighter versions of Ubuntu as well that keep 80% of the Ubuntu goodness and run on 128 MB of RAM.

Of course you can just install Ubuntu in server mode and use:

sudo apt-get install whateverpackageyouneedtoinstall

The advantage of having a gui on the server is you can set up some graphical monitors (like gapcmon to view your powerline history from your UPS, load levels over the past few days, and other things to guage server performance.  You can also test that web pages are working properly and test other graphical clients that are using your services.

Xorg uses 3% of the CPU on a PIII, 500 MHz Dell laptop, as I type this post.  So unless you are running a google server the desktop environment doesn't really kill server performance.

Of course you can always kill the Xserver when running in server mode and run startx when you need the desktop for configuration and upgrade work.

I don't think stability is compromised with the desktop running either.  Sometimes the Xserver will crash with beta programs, but it only takes you to the command line.  A simple startx will get you going again.

For maximum stability, I recommend Dapper Drake, as it will be supported for 5 years.

---

