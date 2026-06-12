---
title: "Using Linux  Ubuntu (5.10) as a Teamspeak server"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by user_of_gnomes on 2006-12-02
Hello, 

I am hoping someone will find the time to talk me through (Step by step, preferably..) setting up a teamspeak server on Linux Ubuntu (5.10) and also explain to me how I can get Linux Ubuntu to automatically update from the command line which is a feature I think is only available when you use the GUI? 

So far I've been messing around with it for over 3 hours but my main source of information, ubuntu's wiki, seems to be down and I haven't got much further than trying to create a new user. Which doesn't even work out for me like it should: 

_[Tutorial: Setting up the TeamSpeak 2 server on Linux](http://www.goteamspeak.com/index.php?page=tutorial_b)_

It doesn't create a home directory but it does create the user I'm not sure how important this is, but I want to be able to use the Linux server in the future as an FTP server so one of my priorities is to keep it tidy.. 

Any guidance is much obliged! 

Here's some information on the system: 

AMD Sempron S754
Asrock K8Upgrade-NF3
WD PATA 6.4GB HDD 
Seagate 320GB SATAII HDD
52X CD-ROM player 
PCI videocard (Trio64 something)

---

### Post by blu.gecko on 2006-12-26
I am getting ready to run teamspeak server on a older machine, any luck or info you could give me?

---

### Post by mystdragon on 2006-12-26
[INDENT]explain to me how I can get Linux Ubuntu to automatically update from the command line which is a feature I think is only available when you use the GUI?[/INDENT]

cron and aptitude are your friends.  I [found a short snippet]("http://wook.wordpress.com/2006/05/12/ubuntu-automatic-update/") online that will probably do what you want.  I would recommend changing the code in question from using apt-get to aptitude, like so:

```
#!/bin/bash
aptitude update
aptitude upgrade -y –force-yes
aptitude autoclean
```

I haven't tested this, so your mileage may vary.

Double check that the home directory is located in /home for the teamspeak user.  If you find it, no problems.  If you didn't, you can fix it very easily:

```
$ cd /home
$ sudo mkdir teamspeak; chown teamspeak:teamspeak
```

That will create a teamspeak directory and change the owner and group to the teamspeak user.

Good luck.

---

