---
title: "sopcast and internet become so slow??"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by tettayes on 2007-11-14
whenever i use sopcast to watch tv online, the internet connection becomes really slow and unstable... so i have to reconnect to the network each time i use sopcast.
has anyone got same problem??

---

### Post by ginjabunny on 2008-01-21
Yes I have noticed similar.

I have Ubuntu server 7.10 running Shorewall firewall, I run p2p tv apps like TVants, sopcast and TVU on a Win PC behind it, and I have noticed that prolonged use of sopcast can make my internet connection unstable and unresponsive, I put it down to that fact that the firewall is getting hammered with requests from other sopcast client trying to connect to my sopcast with it being p2p (that's what logwatch tells me). I have had to restart the server on occasion

I have looked into a few of these apps but none actually explain how I am supposes to share, I think they assume I am on Win and the modify the builtin firewall, but nothing about being behind a firewall and using nat etc. 

I now know what ports they use so in the spirit of p2p I have opened the ports for TVants recently so I am sharing not just leeching, maybe I should try it with sopcast to see if it makes a difference. If I do I'll let you know.

Not much help really just my observations.

---

### Post by MaindotC on 2008-02-28
I experience a big lag as well.  First of all, when I do connect to games, the connection speed jumps up to 100%, and then it slowly starts to degrade to 2 - 3% over a period of about 2 minutes.  Regardless of my connection speed, accessing web pages while sopcast streams is almost impossible.  Always made me wonder how everyone posts on [http://golf.cautela.nl/nhl](http://golf.cautela.nl/nhl) during games but there's little if any mention of latency issues last I checked.

I am a student on a campus that has two DS3 connections to the service provider - almost equivalent of 90 mbps.  That may not sound fast, but I have spoken to the network administrator about the latency issues - I was assuming that sopcast uses so many resources that perhaps the bandwidth manager caps me.  He said he watches the bandwidth manager logs daily and of the 90 meg connection, this campus uses about 20% of it on a daily basis, and there are only capping issues in the 85% range, and he has not seen anything come even close to that.

I run sp-sc and qsopcast on my school-issued Thinkpad T60 w/ Gutsy and it does this.  I installed Fedora 8 on a lab computer - had a perfect install (a lot less issues than I've had with Gutsy, I might add) and it also experienced the same issue.  Like if I remote into my Fedora machine and start Sopcast, I'll lose connection pretty quickly.

I am learning but compared to some of the developers and debuggers I'm a total newb and I'm not really sure how to troubleshoot this issue.  Hopefully more people will have the problem and someone will be able to patch it :(

If anyone has any suggestions on where I should look, please let me know.

---

