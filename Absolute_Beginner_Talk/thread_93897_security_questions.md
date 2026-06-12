---
title: "security questions"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-23
hi, i have just connected to the internet for the first time with Ubuntu. i really like it alot and hope to switch over from Windows.

i'm abit worried about security. should i go and check for OS patches? should i turn off any services? i don't have a router and i want a different FW which will hide my ports, i know it's not the end of the world but that's what i'm used to. should i get any real-time protection? i know nothing about Unix rootkits. where can i find out about basic security? thanks

---

### Post by r4ik on 2005-11-23
[QUOTE=Danielle]hi, i have just connected to the internet for the first time with Ubuntu. i really like it alot and hope to switch over from Windows.

i'm abit worried about security. should i go and check for OS patches? should i turn off any services? i don't have a router and i want a different FW which will hide my ports, i know it's not the end of the world but that's what i'm used to. should i get any real-time protection? i know nothing about Unix rootkits. where can i find out about basic security? thanks[/QUOTE]

Here is a little something to read.
It might have the answers you need.
good luck.

[http://www.ubuntuforums.org/search.php?searchid=2629643](http://www.ubuntuforums.org/search.php?searchid=2629643)

---

### Post by r4ik on 2005-11-23
Gives a dead link on my system now worked before but
if the same happened to you try Search- anti virus.

---

### Post by kont.raen on 2005-11-23
[QUOTE=Danielle]hi, i have just connected to the internet for the first time with Ubuntu. i really like it alot and hope to switch over from Windows.

i'm abit worried about security. should i go and check for OS patches? should i turn off any services? i don't have a router and i want a different FW which will hide my ports, i know it's not the end of the world but that's what i'm used to. should i get any real-time protection? i know nothing about Unix rootkits. where can i find out about basic security? thanks[/QUOTE]

Well first of all - yes - you should check for Updates - or rather Ubuntu will check for updates itself. If it finds any, a message will pop up and notify you whether you want to install them and how to acomplish this.

Concerning services - there shouldn't be much to turn off, as Ubuntu does not come with too many (especially security-critical) running daemons - but if you installed additional ones yourself, you should of course think again :)

As you do not have a router with an included firewall, I think you should install firestarter as a software-firewall, on your system. Just run the forum's search function for more info on this app.

---

### Post by Biased turkey on 2005-11-23
[QUOTE=kont.raen]

As you do not have a router with an included firewall, I think you should install firestarter as a software-firewall, on your system. Just run the forum's search function for more info on this app.[/QUOTE]

A firewall ?  Who need it ?
From the wiki:
Since Ubuntu doesn't run any daemons that listen to the outside world by default (the postfix install only listens on localhost) there's no need for a default firewall.

The rationale is that if a user's got a need for installing a world-facing daemon, they'll be aware that they should configure a firewall/ACL for it too.

I happen to have installed Firestarter  on my Ubuntu rig because I use it as a Firewall-router for my local LAN.
On the other hand, I installed Ubuntu on my mom's rig but without Firestarter because it's just a single system facing the internet.

---

### Post by Danielle on 2005-11-23
thanks for the help. i think i'm going to install the FW mainly because i'd like to get my ports hidden and i'd like to see what's happening with things like icmp 8. i'm not a network expert but i like to play around with it. 

the other things i'd like are an antivirus for on demand scans but with the possiblity to run in real-time and a HTTP proxy like proxomitron, i think it can be made to work with linux.

but, first i have to work out how to reconnect to the internet. i have another thread going for that though, it just wont work :(

---

