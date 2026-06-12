---
title: "Installing NMS software, am I missing something?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by clabrown on 2006-08-24
I'm a bit frustrated so forgive my tone, but maybe I just don't get it. 

Background: I deal most days with windows networks as a consultant, and have "some" LINUX and FreeBSD experience, so editing config files, or the command line doesn't bother me, but I work with computers and don't find them fun like I used to ... I want it to !JUST WORK!! so I can go play golf, the process of making it work no longer holds much jazz for me ... so ... 

I wanted to setup a NMS (Network Monitoring System) so it could tell me what windoz server I needed to go kick in the face before the users asked why they couldn't access whatever. 

I decided to give Ubuntu server a spin, easy to install, zillion software packages ready to install with easy command line or gui tools, what could be easier? 

I researched a bit and decided to test Zabbix, OpenNMS, Nagios, JFFNMS and BigSister. As far as I can tell, some of them aren't in the repositories AT ALL, and only JFFNMS is even close to being up to date. 

Are there other 3rd party repositories where people update the software? Are the "official" Ubuntu repositories frozen 6 months before the actual Ubuntu release? Are the "official" Ubuntu repositories ever updated after the release? 

I uncommented the lines in the config file to get the universe and multiverse. I googled and found Zabbix in the Edgy repository, so I added that, but Aptitude was unable to resolve dependancies with several things "Unavailable" like libc6 >= 2.4-1 ... I didn't really expect the edgy repository to work, just took a shot. 

In the past I have developed software for a living, so I don't look forward to installing and configuring a development environment (a major task in itself), and then trying to get the correct versions of all the dependent sub systems, and then compile everything up to and through MySQL followed by what ever special Ubuntu configuration is necessary for each product to try to build an NMS which I will then wonder if it is running right assuming it compiled without errors. The thought of header files, includes, and dependencies makes my skin crawl just thinking about it. 

So the basic question ... do I just not "get it"? Seems like in my limited experience that the repositories might be a good marketing ploy, but as far as installing up to date network utilities (NMS's anyway) you're pretty much back in the bad old days looking for source code from different sources, hand resolving dependencies between packages and compiling from scratch. I thought that with packages, and RPMs and repositories, the developers and "smart people" ironed out the kinks so "normal" people could just install and use the software with a fair amount of confidence that it would work .... 

Yea,whaaaa, whaaaa, whaaaa I know I'm whining and it's not a pretty site <grin>

---

### Post by steve.horsley on 2006-08-24
Quite a few of the less common applications come only as an RPM, or even as a .tar.gz full of source code. So it's not that unusual.

RPMs can be converted to DEBs by a package called **alien**. Of course, there may be dependency issues.

If you must compile, you can install all the stuff you need with just the package build-essential. Look for posts by aysiu who has a web site on installing (I don't have a reference at the moment).

No, you;re not missing anything. If the software you want hasn't been packaged for Ubuntu, you may have some work to do to get it going.

---

### Post by clabrown on 2006-08-24
OK, so assuming that I decide to take the plunge and try to compile a package, and further assuming that I actually got it to work right (which seems a pretty far fetched idea) would I then submit somehow back as a package so others don't have to endure that pain? 

Or is it pretty much every man for himself after the release ... 

Are the repositories updated or are they frozen with the OS release? 

Are there any more up to date repositories that are maintained by other users or groups if the "official" repositories are frozen some time before the OS release date?

---

### Post by Grifter77 on 2006-09-18
I'm a IT security technician, and just starting to discover Linux. Yes our course are unfortunetly almost all windows oriented.  I love Kubuntu/Ubuntu so I'm geting my brain fried trying things.  You can install the Debian package of Big sister, make sure you install de base package first , then the server and agent one.  It works to a certain extend on my side, but I'm quite sure I screwed up somewhere!!  I'll let you know once everything is installed and working, if you are interested.

lata

---

### Post by clabrown on 2006-09-18
Grifter:

Thanks for the info. I've been busy, and haven't had time to pursue it much further. I found an NMS named Zabbix with the latest version in the Edgy repository, but I couldn't get it to work on dapper. I even tried to install ubuntu edgy, but the installation produced some errors I didn't understand about something else using the package system. 

I'd love to see a HowTo on how you got BigSister working. 

Thanks, Cla.

---

### Post by Grifter77 on 2006-09-20
Zabbix up and running quite fine !!! I'm starting my Big Sister from scratch.

_For Zabbix start by reading this and make sure LAMP works otherwise nor will Zabbix or Big sister work : _

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

  
Then go to the Zabbix website [www.zabbix.com](www.zabbix.com) and donwload the sources.
Follow there instruction carefully everything there.

If you run into errors google it you'll find the answer or post it here there is a good chance I ran into it!

---

