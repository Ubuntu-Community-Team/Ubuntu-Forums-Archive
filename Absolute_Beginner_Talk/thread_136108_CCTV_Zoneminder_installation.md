---
title: "CCTV Zoneminder installation"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by total numptys mate on 2006-02-25
Hi all

I am hoping someone may help here - i have been trying to install Zoneminder cctv software for sometime now without success, has anyone instaled this on ubuntu and if so any chance of a step by step guide please.:-D 

Any help would be great..

Mark.

PS. As the name indicates i am a totally newbe to the linux world, Microsoft has been my world since dos:-k

---

### Post by total numpty on 2006-03-01
I dont think anyone on here can do it or is interested and thats why there is no response mate.:confused:

---

### Post by Andrew1234 on 2006-06-18
Have a look at this link in ZM forum, I been looking to this but not tried to install yet!

[http://www.zoneminder.com/forums/viewtopic.php?t=6139&highlight=ubuntu](http://www.zoneminder.com/forums/viewtopic.php?t=6139&highlight=ubuntu)

It may help!

---

### Post by perspectoff on 2007-03-31
.

---

### Post by stever26 on 2007-04-03
Hi

I have been doing a lot of research on installing ZoneMinder 1.22.3 on Ubuntu Edgy and everything I find points to the same 6.06 install instructions used by perspectoff above and a small script mod to get ZoneMinder started in 6.10.  However, these instructions don't seem to work for me and I'm getting errors that no one else posts about.  Normally I would just keep trying and wait it out until I found a solution but last night someone tried to steal my car right in front of my house and had I got this software running over the weekend I might have been able to do something about it.  Any help would be much appreciated.

The install seems to go along just fine.  The only configure warnings are about not finding gawk (which I do have the latest version of according to apt), no perl module X10::ActiveHome, no perl module Device::SerialPort, and no  pcre/pcre.h.  It finishes the configure process just fine and installs just fine.  However, when I go to start it I get the following:

```

# /etc/init.d/zm startStarting ZoneMinder: Warning, overriding installed ./zm.conf file with local copy
Can't open config file '/usr/local/etc/zm.conf': Permission denied at /usr/local/share/perl/5.8.8/ZoneMinder/Config.pm line 100
BEGIN failed--compilation aborted at /usr/local/share/perl/5.8.8/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/local/share/perl/5.8.8/ZoneMinder.pm line 33.
BEGIN failed--compilation aborted at /usr/local/share/perl/5.8.8/ZoneMinder.pm line 33.
Compilation failed in require at /usr/local/bin/zmdc.pl line 50.
BEGIN failed--compilation aborted at /usr/local/bin/zmdc.pl line 50.
failure

```

Also if I go to the webpage in firefox I get:
```

Warning: fopen(/usr/local/etc/zm.conf) [function.fopen]: failed to open stream: Permission denied in /var/www/zm/zm_config.php on line 26
Could not open config file.

```

ok so I said to myself obviously there is a file permission problem here right? I proceeded to change the permissions of all the files mentioned in the errors but to no avail.  Basically I am stumped at this point and I am reaching out to the community in hopes that someone has had the same problem or knows what might be going wrong here.  It may also help to point out that I am fairly inexperienced with Linux in general and very new to Ubuntu (running it for about 3 weeks now). 

Thanks,
Steve

---

### Post by Joey French on 2007-04-03
I have installed zm via their instructions for dapper, even though I run Feisty. I got it working, and it performs, but it is always a pain, and I get complaints all the time during boot and such. Best thing I can tell you is to just setup a dapper box and use the instructions via the zoneminder wiki (until install instructions become more mature).

Joey

---

### Post by stever26 on 2007-04-04
Joey,

Well since you got it running maybe I'll upgrade to Feisty this weekend and give that a shot.  I would hate to revert to an older distro and possibly break other already working packages.  I'm pretty sure the only thing I'll loose going to Feisty is the hard drive temperature monitor (hddtemp).  Thanks.  If anyone else has ideas for fixing the current errors though I'm still interested.

Thanks,
Steve

---

### Post by Joey French on 2007-04-07
You should be able to get it working following the Dapper instructions on the ZM wiki. I think the only thing that is a problem is that it asks for one package that has been changed to a higher version number. I have it running on a dapper box I haven't touched in a long time, and it works perfectly following the zm wiki instructions.

Good luck.

Joey

---

### Post by blackest_knight on 2007-04-08
glad to see i am not the only one trying to run this on feisty 

the instructions you refer  to are these?

[http://www.zoneminder.com/wiki/index.php/Ubuntu_6.06_-_Dapper](http://www.zoneminder.com/wiki/index.php/Ubuntu_6.06_-_Dapper)

I seem to get stuck here 

mysql mysql < db/zm_create.sql

mysql mysql

mysql> grant select,insert,update,delete on zm.* to 'zmuser'@localhost identified by 'zmpass';

mysql> quit

mysqladmin reload 

i think i need to create a mysql user but i don't know how

---

### Post by stever26 on 2007-04-08
Ok so I upgraded to Feisty and boy was that a bad experience.  X wouldn't start when I rebooted.  I was getting a "no screens" error.  I am running a mini-itx board with via chips so I should have realized I would have some problems.  Anyway, after much hassle I found out that I could change the drivers back to the standard vesa ones and get X to start.  Then I had to reinstall the openchrome drivers that I was using before the upgrade.

I now have Feisty running properly and I tried to install ZoneMinder again but unfortunately I get the same errors as in my first post.  I think I might give up at this point.  Does anyone know of any simpler network camera recording software?  All I really need is a daemon to record from an Axis network camera and it should have the ability to do motion detection.

blackest_knight - I was using [http://www.zoneminder.com/wiki/index.php/Ubuntu_6.06_-_Alternate](http://www.zoneminder.com/wiki/index.php/Ubuntu_6.06_-_Alternate) .  Not that I would be able to help because I'm kinda new to all this, but you would have to give more info about the problem you are having.  Are you getting errors when you run the commands? Which command is causing the problem? etc.  All I can suggest with the info given is make sure you are root and maybe remove the first occurrence of "mysql" from the first command.

Steve

---

### Post by jethro10 on 2007-05-10
This seems to be a 7.04 installation guide on the Zoneminder website, with a new deb.

[http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04](http://www.zoneminder.com/wiki/index.php/Ubuntu_7.04)

J

---

