---
title: "Can't get internet working!"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by hollym on 2006-09-06
Howdy to all! Have just installed Ubuntu for the first time and it seems very nice, aside from the fact that nothing really works (internet, sound, video, music, all not working). First of all however, I would like to get the internet working.

I am connected directly to the net via a Local Area Network (I just plug it into the wall and it works (in Windows at least). I have never had a problem in Windows, it always work straight away from install with no other configuration. I have no idea about DNS information but have more or less a static IP (changes every couple of months or so). When I type in ifconfig, i get a result for eth0 and something else (cant remember)

When I check the System monitor in Ubuntu, it seems as though there is some minimal network activity (i.e. the are some packets both being sent and received). However, when I open firefox there is no joy.

Not being well versed in linux, I'm not sure where to start. Any suggestions? cheers in advance ...

---

### Post by jorn on 2006-09-06
Is your card enabled in
System>Aministration>Networking?

---

### Post by hollym on 2006-09-06
are you talking about the Ethernet Interface ... eth0? If so, then yes, that is enabled.

---

### Post by hollym on 2006-09-06
or is there something else I should be looking at ... it doesnt seem to be rocket science, and everything seems ok, just getting nothing from the browser ... (or maybe any other program requiring a network, not sure!)

---

### Post by deadgobby on 2006-09-06
Are the network setting are DHCP or static. Are you in collage and cannot conect to the schools network?

---

### Post by hollym on 2006-09-06
My network setting are DHCP (which it is set to in Networking). No, i am not in college. The building I live in has broadband wired into each apartment and a central server box in the basement. 
Am I Correct in assuming the newtork is active given that System Monitor indicates some bytes being received? Would a ping tell me if the connection is working? If so, what is an appropriate address to ping?

---

### Post by deadgobby on 2006-09-06
[https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28DHCP%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28DHCP%29)

---

### Post by hollym on 2006-09-06
ok, thanks for the post ... any ideas about how to obtain DNS information ... I've never had to deal with this in windows, just works straight from install. I live in South Korea and English technical support is all but non-existent.

---

### Post by Apple 101 on 2006-09-06
In Windows: Start --> Run --> cmd (command).  Type *ipconfig /al*l and copy down the network settings for your LAN card.  Insert the DNS settings into Ubuntu.

---

### Post by hollym on 2006-09-06
great, thanks for your help ... ill give that a go and hopefully all will be well.

---

### Post by hollym on 2006-09-06
have found out the information required. however, the files to edit are read-only. apparently i cant save them, apparently i dont have enough permission. any help please!

---

### Post by Apple 101 on 2006-09-07
Input the information to System --> Administration --> Network.

To edit the files in a terminal command prompt environment: *gksudo gedit <path to filename>/<filename.filename>*

---

### Post by blunt1 on 2006-09-13
:confused: im a beginner too, i cant connect to the internet!

i am running two pcs off a d-link router win xp working fine and ubuntu nothing at all!

can anyone talk me through some step by steps?!

Much appreciated all,

J

---

### Post by blunt1 on 2006-09-13
> **hollym said:**
> Howdy to all! Have just installed Ubuntu for the first time and it seems very nice, aside from the fact that nothing really works (internet, sound, video, music, all not working). First of all however, I would like to get the internet working.

I am connected directly to the net via a Local Area Network (I just plug it into the wall and it works (in Windows at least). I have never had a problem in Windows, it always work straight away from install with no other configuration. I have no idea about DNS information but have more or less a static IP (changes every couple of months or so). When I type in ifconfig, i get a result for eth0 and something else (cant remember)

When I check the System monitor in Ubuntu, it seems as though there is some minimal network activity (i.e. the are some packets both being sent and received). However, when I open firefox there is no joy.

Not being well versed in linux, I'm not sure where to start. Any suggestions? cheers in advance ...
im a beginner too, i cant connect to the internet!

i am running two pcs off a d-link router win xp working fine and ubuntu nothing at all!

can anyone talk me through some step by steps?!

Much appreciated all,

J

---

### Post by pravuil on 2006-09-13
Did you try to configure the network connection without a default route during the installation process? Type ifconfig in a terminal and copy the results onto this thread.

Also the router itself might have a problem with handling ipv6. There is a workaround in this thread. Just have to search for it though.

---

### Post by gt900 on 2006-09-13
ok few things 

ifconfig

is there and ip address showing in there?

basics of how internet works in unix 
hosts dns = how to get the ipaddress
default gateway = how to get there
ifconfig is the tool to show you if the interface is up or not and if it has and ip address
try this command 
ping [www.google.com](www.google.com) 

Does it say host unknown? if it does then no dns is not working.

if it does say and ipaddress and gives results then dns and default gateway are working.

You may have to use a proxy in your firefox web browser in xp it can be autoconfigured but I dont if firefox does the same.

---

