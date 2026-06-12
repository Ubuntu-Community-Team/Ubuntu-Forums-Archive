---
title: "POSIX: no route to host"
date: 2012-02-15
forum: Apple Hardware Users
---

### Post by computerfox on 2012-02-15
Hello everyone, let me start by apologizing for my attitude last time I was around.  I just just frustrated and it was wrong of me to take it out on you guys. (Referring to my server-email question).

Anyway,  I am back because I keep getting this ridiculous issue with my network.  

Problem statement: Whenever I go into Cydia to check my repository, it does read in all of my packages, but when I want to install one of those packages, it gives me the POSIX error that there is no route to the host (my server).

Specs:

Server 1-> Runs on port 80, Has Mac OSX Lion, uses webmin for administration, can not run dpkg-scanpackages correctly therefore i have server 2

Server 2-> Runs on port 8080, has Ubuntu server 6, is a g3 power mac, uses webmin for administration, i can run dpkg-scanpackages correctly

Network-> both ports are open and functional outside of my local network, just not in cydia

Disclaimer: Please, don't mention changing my server 2 because I don't have a second server, have no interest in purchasing a new one, and it can only run Ubuntu server 6 since it's a G3.

More information for the repo: [http://repo1138.computerfoxdesign.com:8080](http://repo1138.computerfoxdesign.com:8080)

NOTE: the domain for computerfoxdesign.com is on server 1, but i can access the repo in safari, just not in cydia.

Food for thought: Could it be possible that Cydia doesn't like port 8080 in the URL?

I tried changing it to server 1, but it still gives me that error.

Any thoughts?

---

### Post by computerfox on 2012-02-15
> **baozaleng said:**
> thanks

?

---

### Post by computerfox on 2012-02-16
Any ideas?

---

