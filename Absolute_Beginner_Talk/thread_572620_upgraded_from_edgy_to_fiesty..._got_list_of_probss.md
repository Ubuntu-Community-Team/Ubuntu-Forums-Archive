---
title: "upgraded from edgy to fiesty... got list of probss..confused pls help"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by ishwar on 2007-10-10
hi i was using ubuntu 6.04 for a year..

i upgraded in an official way to fiesty. spent an entire night doing it!! 

the problems which i found are 
1. when i run update manager ,, its not installing i have to manually give it a command well, i dont know exactly what im doing but this is what is happening!

could not read network connection list.
/home/eswar/.DCOPserver_my wireless weardness_0
please cheack that the "dcopserver" program is running.

reading package fields....done
reading package status.. done
retrieving bug reports.. 0% W: unsupported proxy 'false'
Abort the installation [Y/n]?n
retrieving bug reports.. done
parsing found/fixed information... done
reading data base.......



Kaffeine problems...  -- not initialising!!

wireless weardness:~$ sudo apt-get install kaffeine
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  kaffeine-xine
The following NEW packages will be installed
  kaffeine kaffeine-xine
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3177kB of archives.
After unpacking 6844kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... 0% W: unsupported proxy `false'
Error retrieving bug reports
Retry downloading bug information?[Y/n]? y
 W: unsupported proxy `false'
Error retrieving bug reports
Retry downloading bug information?[Y/n]? n
Abort the installation[Y/n]? n
Retrieving bug reports... Done
Parsing Found/Fixed information... Done
Selecting previously deselected package kaffeine-xine.
(Reading database ... 168846 files and directories currently installed.)
Unpacking kaffeine-xine (from .../kaffeine-xine_0.8.5-0ubuntu1~feisty1_i386.deb) ...
Selecting previously deselected package kaffeine.
Unpacking kaffeine (from .../kaffeine_0.8.5-0ubuntu1~feisty1_i386.deb) ...
Setting up kaffeine-xine (0.8.5-0ubuntu1~feisty1) ...
Setting up kaffeine (0.8.5-0ubuntu1~feisty1) ...

eswar@my wireless weardness:~$ kaffeine
/usr/bin/iceauth: /tmp/dcopPfMg8b:1:  bad "add" command line
/usr/bin/iceauth: /tmp/dcopPfMg8b:2:  bad "add" command line
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
kdeinit: DCOPServer could not be started, aborting.
ERROR: KUniqueApplication: Can't setup DCOP communication.

---

### Post by ishwar on 2007-10-11
i have solved the kaffeine problem!! 

i guess i have changed the name in domain!! i dont know how it works but .. i changed my name in setting.. i dont even remember where i did.. 

but i still have the problem of bug reporting sort of question when i install any thing with apt or synaptic.. i have to open the terminal option and choose no option for bug reporting and install manuelly.. is that a buy .. do i need to report this!! 

pls let me know

ishwar

---

### Post by AlexenderReez on 2007-10-11
what kind of wireless card are you using...?i doubt it is internet problem related...

what is your internet setting..?

[PHP]cat /etc/network/interfaces [/PHP]

---

### Post by ishwar on 2007-10-11
hi this is my output!! thank u!

cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp





eswar@eswar:~$

---

### Post by ishwar on 2007-10-12
hi my kaffine and xine players seems to have probs .. they are filled will small dots.. i have attached the appearance .. can any one had this problem..


in all videos!! i mean all formats.. which use to play very well when i was using ub 6.04!!!

pls help.. i dont want to damage my hardware!! is that serious problem or just needs adjustment!

cheers
[IMG]/home/eswar/Desktop/problems.png[/IMG]

---

### Post by OldTimeTech on 2007-10-12
What kind of video card do you have?

It  may need to have the drivers loaded out of the repositories to run without the dots....or it may be that your video card is actually dying and you need a new one.

---

### Post by ishwar on 2007-10-12
okay now i m scarred.. 

the problems i have observed!!1

1. when i play in kaffeine plays the movie well but leaves this dot all the time
2. when i try movie player starts playing without the dots clearlly,, but when i try to manipulate any thing like adjusting the screen size or forward the movie with bar..etc.. i lose the video and only sound[Ubuntu Forums - Reply to Topic]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3510560") works... 
i recently installed awn-manager and affinity.. does this have any effect on my videocard memory -- i got 512 memory which is shared with video card.. 
/home/eswar/Desktop/my video card1.png
/home/eswar/Desktop/myvideocard2.png

does it help!! cld u see the pics

---

### Post by ishwar on 2007-10-12
hi sorted out my problem with the kafine and xine player.. i had to choose my video drive properly.. in my case it was OSD.. and everything bak to normall . thanx for u r suggestion thought..

---

