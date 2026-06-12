---
title: "unanswered questions??"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by satelight 7430 on 2007-09-30
hello to all here.

Been using fiesty 7.04 for the last month or so. dont ever plug in my windows disk any more. I've been searching & reading this and other forums  since i made the change. now i begin to wonder certain things(differences) between this (linux) & windows. ok to start this out i see that antivirus & firewall software can be run on ubuntu?? I was under the impression that as long as i watch where i go & what i read that i dont need this stuff. 

in win$ it just took up lots of processor & ram power just to run this stuff(trying to protect myself from the worst). This is one reason why i've made the switch. Also anothe rreason was that i figured that since the internet (backbone) is wrote in linux(unix) that it would play alot  nicer together but when i open my browser & load my first page i see my network resorces peak & also lag for a few seconds(getting worse lately). 
I have a decent connection 8000/768, so i'm haveing a problem beliving its my connection!! and my hardware is no slowch, 1.83 duel core 7200 hd  and diecent vid card also 2 gig ram.
So it hard for me to believe its any of this thats the bottleneck in watching my sys moniter,all is running well. so far i love it just wondering about this stuff.

Also last but not least the shareing stuff!! My home is set-up as a network with snap stream media server & tied together(tv watching,blah,blah) and I know that I'd love to turn my so called server into a linux but the hassle of it let alone the time we've be with out it( the wife & kids) might push me over the edge i tellyou!! as i'm sure lots of people out there deal with the same thing. the only time i get with that machine (to update & work on is after 10:00pm then only for a couple hours to clenup & defrag ect...
so do i need this stuff on a ubuntu machine?? is it possible to network so all can use easyly and last but not least server question??

Above this stuff I love my fiesty with beryl and everything.this forum is fantastic and so far all i need to do is come here & do some searching & i get a answer. sorry about being such a noob with some of this stuff but looking for some advice & a direction for the future. thanks to all that respond:)

---

### Post by dwhitney67 on 2007-09-30
Jeez it's hard to read your ramblin' post.  Are you asking if you need anti-virus s/w on your Ubuntu system?  The answer is "no".  Are you asking if you need a firewall?  One is already built-in.

One thing I can assure you... the Ubuntu forum will not be able to help you manage your domestic issues with your PC usage.  I recommend you pick up a 2nd-hand PC and set that up as a server, or as a platform on which to learn Linux.

Good luck with everything.

---

### Post by Perfect Storm on 2007-09-30
> antivirus & firewall software can be run on ubuntu?

Not needed for normal users. There are anti-virus applications out there, if you're running e-mail server(s) or setting up Lan where you have to protect you windows machine(s).

Ubuntu comes with all ports closed by default and with IPtablets, if you want a frontend for it you can install firestarter.


Which video card do you have?


Ubuntu (or linux in general is self-maintaining. The only thing you might want is to clearing your browsers cache and your downloaded packages via synaptic/apt-get/aptitude/add-remove with this command;
```
sudo aptitude clean
```
That should be it.

---

### Post by Sef on 2007-09-30
> . the only time i get with that machine (to update & work on is after 10:00pm then only for a couple hours to clenup & defrag ect...

There is no need to defrag Linux.  Ext3 will do it every 30 boots and Reiferfs don't need to be.

---

### Post by ramjet_1953 on 2007-09-30
You may speed up your Internet experience by disabling IPV6.

If you do a search on these forums, you will find a tutorial on how to do it.

Also if you configure your router to use Open DNS things will also work a bit quicker.

[http://www.opendns.com/](http://www.opendns.com/)

Regards,
Roger :cool:

---

### Post by satelight 7430 on 2007-09-30
ok , thanks to all that have givin there 2cents!!
i read that i dont need av or firewall(it built in) but I,m being told that ubuntu 
defrags every 30 reboots or so?? my main pc does'nt ever shut off. if anyone intrested wants to visit snapstream software they'll understand why.its being used as a front end for my television. it also send the siginal from it to 3 other machines. its also has music stored there,pictures,videos,letters,dvds.
everything that is entertainment related. so i believe it's being used as a sever, right??? tell me if i'm wrong please. i know i can ramble on but there's alot going on here so i get befuddled some times.
thanks again for help in my  maddness!!

---

