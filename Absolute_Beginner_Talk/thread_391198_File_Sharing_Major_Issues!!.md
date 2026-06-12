---
title: "File Sharing Major Issues!!"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by 2nvme on 2007-03-22
Hi! I'm very new to Ubuntu. I've only known Windows, and I'd like to think I'm a pretty savvy and curious computer person. But, I have to admit Ubuntu has gotten me soooooo frustrated and annoyed I really just want to cry!

I have, for the past 3-5 days, been trying to download music. Now, I installed GTK-Gnutella to do the job. At the beginning, I was able to just open the program. I tried to search for a random song, just to see if it worked. Nothing. Kept saying I was behind a firewall. I don't have a firewall. So I tried getting help on this forum. Every suggestion I found did not work. Now I can't open the program at all. So I removed it and tried Frostwire. Thing is I need Java Sun 5.0. Downloaded Java Sun...at least I thought that's what I did. Now every time I try to install or remove a program I get the same Error message: 

E: sun-java5-doc: subprocess post-installation script returned error exit status 1

So I tried the forum again, and was given a set of instructions that led me to the website to download the documentation, but that didn't work either.  So I removed Frostwire and Java Sun 5.0 and returned to the forum to see if there's anoter program I can use to download music. Ktorrent came highly recommended, so I installed it.

I can open the program, but I had to install the help center cause I couldn't figure out how to use the program. Unfortunately for me, the help center can help me with every imaginable K-type program, but nothing on how to actually use Ktorrent.

Can someone...anyone please lend me a kind hand? I'm at my wits end here. With everything else, Ubuntu has been great, but this MAJOR issue is driving me to drink!! :confused: :cry:

---

### Post by SwedishHatFaction on 2007-03-22
I'm new to this whole Ubuntu thing as well but back on Windows, I used Azureus for all of my torrenting, and the setup and interface is fairly simple and straightforward. However, I'm running into the same "firewall" issues and I have no idea how to remedy that. Some help would be greatly appreciated.

This is the Azureus website if you are interested:
[COLOR="Blue"][http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)[/COLOR]

And here's the wiki for additional help.
[COLOR="Blue"][http://www.azureuswiki.com/index.php/Main_Page](http://www.azureuswiki.com/index.php/Main_Page)[/COLOR]

---

### Post by AndyCooll on 2007-03-22
Firstly, you ARE behind a firewall, since Ubuntu by default closes all ports. You might find reading up about IP tables worthwhile. However, installing Firestarter as a graphical interface to IP tables might help.

Did you use Synaptic to install Java? It might actually be worth your while using Automatix ([www.getautomatix.com](www.getautomatix.com)) to get you going with Frostwire. This program takes the pain out of installing a few basic apps.

:cool:

---

### Post by AndyCooll on 2007-03-22
> **SwedishHatFaction said:**
> I used Azureus for all of my torrenting, and the setup and interface is fairly simple and straightforward. However, I'm running into the same "firewall" issues and I have no idea how to remedy that. Some help would be greatly appreciated.

Azureus presented me with problems too. I resolved this by forwarding ports on my router.

:cool:

---

### Post by xurizaemon on 2007-03-23
> **AndyCooll said:**
> Firstly, you ARE behind a firewall, since Ubuntu by default closes all ports. You might find reading up about IP tables worthwhile. However, installing Firestarter as a graphical interface to IP tables might help.

FireStarter is good, but there is a difference between having no open ports, and firewalling (with or without iptables). As I understand it - perhaps I'm wrong or out of date - Ubuntu ships with no open ports (and no iptables rules).

I may well be wrong though ... it's been a while since I did a fresh install of Ubuntu Desktop, things may have changed. 

Agreed taht FireStarter is a good tool, if you want a graphical firewall configuration.

---

### Post by seshomaru samma on 2007-03-23
Hi
I use azureus

a side notice - many skilled windows users find linux difficult because they expect to achieve the same level they had after several years of windows in a few days of linux. you may not realise it but for some people installing java in windows is difficult, of course once you know how to do it and you've done it several times it becomes much easier. linux is the same -except there is much more to learn cause it can do more things than linux. try to take it slow . you will get it working eventually.

what the posts above said is true - you are behind a firewall
installing java with synaptic or apt-get is best
if you use edgy - read[ this ]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")
if you use dapper - read[ this]("http://doc.gwos.org/index.php/DapperGuide")

good luck

---

### Post by nudnik on 2007-03-23
> **2nvme said:**
> Hi! I'm very new to Ubuntu. I've only known Windows, and I'd like to think I'm a pretty savvy and curious computer person. But, I have to admit Ubuntu has gotten me soooooo frustrated and annoyed I really just want to cry!

I have, for the past 3-5 days, been trying to download music. Now, I installed GTK-Gnutella to do the job. At the beginning, I was able to just open the program. I tried to search for a random song, just to see if it worked. Nothing. Kept saying I was behind a firewall. I don't have a firewall. So I tried getting help on this forum. Every suggestion I found did not work. Now I can't open the program at all. So I removed it and tried Frostwire. Thing is I need Java Sun 5.0. Downloaded Java Sun...at least I thought that's what I did. Now every time I try to install or remove a program I get the same Error message: 

E: sun-java5-doc: subprocess post-installation script returned error exit status 1

So I tried the forum again, and was given a set of instructions that led me to the website to download the documentation, but that didn't work either.  So I removed Frostwire and Java Sun 5.0 and returned to the forum to see if there's anoter program I can use to download music. Ktorrent came highly recommended, so I installed it.

I can open the program, but I had to install the help center cause I couldn't figure out how to use the program. Unfortunately for me, the help center can help me with every imaginable K-type program, but nothing on how to actually use Ktorrent.

Can someone...anyone please lend me a kind hand? I'm at my wits end here. With everything else, Ubuntu has been great, but this MAJOR issue is driving me to drink!! :confused: :cry:

Please dont cry in front of the penguins. :) 

There are only two bittorrent clients which work reasonably well with Ubuntu (regardless of hardware and without extensive modification); Bittornado, which is in the repositories, and the new Deluge client which is available here: [www.getdeb.net](www.getdeb.net)  Of these two, Bittornado is the only one which seems to work well regardless of hardware and/or other issues. Unfortunately, Bittornado only allows a single download at a time, making it inefficient when compared to Utorrent and Azureus, which are of course Windows clients, and only seem to work properly under Windows. 

To install Bittornado open a command line, go root to avoid potential permissions annoyances, and type the following:

sudo apt-get install bittornado-gui

I would also suggest installing the additional packages the manager suggests, but doesnt install by default as there is often a good reason for the suggestion. 

To install Deluge (which is very much like Azureus), navigate to the site I suggested, search for the package "Deluge" and when you have clicked on the download link, choose the option of opening the file with the GDebi package installer. Give it the necessary permissions, allowing to download the dependencies, etc and it should all go smoothly. A word of caution: You should have a modern, relatively quick processor to run Deluge properly. I have attempted to run it on machines with CPUs rated under 600Mhz without success. (100% CPU usage and no activity.)

---

### Post by jms1989 on 2007-03-23
I use KTorrent for my torrenting needs.

---

