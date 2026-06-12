---
title: "Brindled's Synopsis"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Brindled on 2006-02-03
let me start off here: i have had an XP (180gig) machine for a year, and now i am using ubuntu w/ a 20 gig partition using the Grub loader. i like it... i was using it on the web w/ very few clicks and i already am a firefox user. i've used L redhat 3 & 7 at various times before, but this one seemed more up too par w/ a noobified enduser like myself. regardless, i play battlefield2 everyday, well except today. ubuntu has caused some very odd problems with my current setup, networking issues mainly. when i boot, and i have to choose so, into windows i have no connectivity to the internet. although every bit of my connection is there. i have checked and rechecked every setting i can that ubuntu could possibly do to keep me from have access.

on the other hand i have a question. i have another computer at my disposal that i am thinking of designating as a linux server for my household. my question is: can you have a linux server, which has usb inline from the cable modem, then have ethernet out to a 8 port switch. the swithch then effectively splits the access up amongst users/cpu's . (i understand there are many ways of networking, but this is the way i prefer) is this even possible?

i ask before i begin backing up gigs and gigs of data. any attention/oppinions are welcomed. thank you

---

### Post by steve.horsley on 2006-02-03
[QUOTE=Brindled]let me start off here: i have had an XP (180gig) machine for a year, and now i am using ubuntu w/ a 20 gig partition using the Grub loader. i like it... i was using it on the web w/ very few clicks and i already am a firefox user. i've used L redhat 3 & 7 at various times before, but this one seemed more up too par w/ a noobified enduser like myself. regardless, i play battlefield2 everyday, well except today. ubuntu has caused some very odd problems with my current setup, networking issues mainly. when i boot, and i have to choose so, into windows i have no connectivity to the internet. although every bit of my connection is there. i have checked and rechecked every setting i can that ubuntu could possibly do to keep me from have access.[/QUOTE]
It is remotely possible that Ubuntu is leaving the hardware in a state that windows doesn't like. You could try turning the PC off completely and then booting into windows without letting it go into ubuntu first.
> 
on the other hand i have a question. i have another computer at my disposal that i am thinking of designating as a linux server for my household. my question is: can you have a linux server, which has usb inline from the cable modem, then have ethernet out to a 8 port switch. the swithch then effectively splits the access up amongst users/cpu's . (i understand there are many ways of networking, but this is the way i prefer) is this even possible?

This is called connection sharing. It is possible, and I'm sure there are many HOWTOs available on the net, but I haven't done it myself so can't talk details. You will probably end up installing a firewall like smoothwall, shorewall, guarddog/guidedog to do the configuration for you. All of these firewalls are GUI front-ends to the Linux command-line firewall module which is called iptables.

---

### Post by Brindled on 2006-02-03
thanx S.H., i figured my nonconnection problem, once booted into xp, was due to some kind of bios setting or networking setting, but for the life of me cannot find the issue. 

for that matter, i cannot find how to make this linux-boot i am running right now extend internet connection to the outlying computers on my switch. there are two xp puters and one imac on my network. my usb is eth1 and my ethernet is eth0.
[[IMG]http://img525.imageshack.us/img525/8436/2networkdevicerecognition9tu.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=2networkdevicerecognition9tu.jpg)
[[IMG]http://img525.imageshack.us/img525/6407/2networksettings3yv.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=2networksettings3yv.jpg)

do you see anything i am doing wrong? this is frustrating, but i want to make it work, w/ or w/o XP.

---

### Post by Brindled on 2006-02-05
anything? this is driving me crazy. and its not like i havent been trying to research it myself. does anyone know of any problems between establishing a connection w/ linux in a dual boot that ceases windows' ability to make a connection. i have searched just about every networking option there is and i cant make WinXP connect or make linux my new gateway, having it serve up a network. please help me!

---

### Post by Brindled on 2006-02-05
[QUOTE=steve.horsley]It is remotely possible that Ubuntu is leaving the hardware in a state that windows doesn't like. You could try turning the PC off completely and then booting into windows without letting it go into ubuntu first.[/QUOTE]
is this possible with the grub loader the first thing that pops up? because, i can choose to boot into xp w/ the grub loader, but this doesnt help things at all. thanx again for your attention.

---

### Post by lila on 2006-02-05
hello,
I have never tried to dual boot anything, so can't help you there, but I am currently looking into getting broadband and from all I have found it is VERY difficult to get a USB modem working with Linux (any Linux).  The trick seems to be using an ethernet modem, and then apparently there are no problems (once you have your ethernet configured properly that is... If you then want to share it with other machines, you just need a hub.
I hope someone else can help you with the dual boot thing, sounds frustrating.
:???: Lila

---

### Post by Brindled on 2006-02-05
thanx for your reply, here is the weird thing: my bios is saying a totally different time and date. and when i choose to boot windows it keeps that same incorrect time/date. however, when choose to boot ubuntu the date/time are correct. wtf, its like it is opposite day or something.

i am gonna pull my hair out!

---

