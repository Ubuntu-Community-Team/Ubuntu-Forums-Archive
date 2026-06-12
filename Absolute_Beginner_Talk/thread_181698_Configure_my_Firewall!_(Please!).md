---
title: "Configure my Firewall! (Please!)"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-24
okay i gotta admit i know very little about firewalls/ports and the like.  i do know that firestarter is a gui for iptables, so at least that. what i dont know and i would like to know, is what port names are and which ones to allow/deny because i want the default to be "restricted" in firestarter.  
by port names, i mean for example :  
HTTPS  =  ?
DNS = ?
etc.

---

### Post by meng on 2006-05-24
[This]("http://www.spirit.com/Resources/ports.html") may be a start. I know it doesn't answer the second part of your question, it's just a start.

---

### Post by user1397 on 2006-05-24
[quote=meng][This]("http://www.spirit.com/Resources/ports.html") may be a start. I know it doesn't answer the second part of your question, it's just a start.[/quote]
That's definitely a start for me! thanks for that, meng.

---

### Post by user1397 on 2006-05-24
Maybe this will help:
Here's a list of the things i use in the internet, and their respective ports (according to firestarter): I use firefox to browse the web, (i guess that would be ports HTTP (port 80) and HTTPS (port 443)), i use FTP (ports 20-21), I use samba (ports 137-139, 445), my network is DHCP (ports 67-68), I use bittorrent (ports 6881-6889), and i use aim/msn/googletalk/yahoomessenger (i dont know the ports for these)
so if i put "restrictive by default" in the outbound traffic policy tab in firestarter, all i would need to do is allow these ports and then i would have a more secure system, right???

---

### Post by nalmeth on 2006-05-24
You gotta do all the homework yourself, but sounds like you have made a good start.

FYI I've read that that port range is not recommended for bittorrent, even though it is the default range for most bittorrent clients.

In azureus, if you go into settings there is a link that explain's that the 53,000 to 64,000 range is much better, as your system is already using the 6881 port. 

I can't dig up the link ATM but will forward it if I do.

Consider changing your bittorrent ports

BTW great indication of the subdued demeanor of these forums, you have not been flamed with RTFM or STFW (or something similar) for your thread title. 

Instead you were provided a useful link. Whaddya know :)

---

### Post by meng on 2006-05-24
I wouldn't dare flame a member of the green team!

Actually I hope I don't flame anyone!

---

### Post by user1397 on 2006-05-24
[quote=nalmeth]You gotta do all the homework yourself, but sounds like you have made a good start.

FYI I've read that that port range is not recommended for bittorrent, even though it is the default range for most bittorrent clients.

In azureus, if you go into settings there is a link that explain's that the 53,000 to 64,000 range is much better, as your system is already using the 6881 port. 

I can't dig up the link ATM but will forward it if I do.

Consider changing your bittorrent ports

BTW great indication of the subdued demeanor of these forums, you have not been flamed with RTFM or STFW (or something similar) for your thread title. 

Instead you were provided a useful link. Whaddya know :)[/quote]
Even though I'm a member of the green team and have 624 beans, i don't know what RTFM or STFW mean!!!:(

---

### Post by meng on 2006-05-24
Oh well, really you should find out on your own. But I just gotta "show off" since I know:
RTFM is read the ferknerkling manual.
STFW is search the ferknerkling web.

And I believe:
AIM: 5190
MSN: 1863
Yahoo: 5050

---

### Post by nalmeth on 2006-05-24
>  RTFM is read the ferknerkling manual.
STFW is search the ferknerkling web. One way to put it I suppose :) well said I didn't want to be rude and say it myself.

You're bean's are skyrocketing erik, keep doing the good work. 
I've never been donned a team-hat before, and I tend to think I'm here a lot. You must really be helping out.

Granted, some times I spend all day, then go a week or two without an appearance. Too inconsistent :-k

---

### Post by user1397 on 2006-05-28
so i have chosen "restrictive by default" with the following services allowed:
HTTP
HTTPS
FTP
SAMBA
AOL IM
MSN IM
DHCP
all of these are set to "when the source is: anyone"
does all of this sound good and safe?  do I need to open some other ports that are important/essential/common?

btw, i use ftp just to upload files to my website, and to upload files to ubuntuforums (like screenshots) i guess;
i use samba for my local network with windows pc's;
my network is DHCP

---

### Post by dmizer on 2006-05-29
[QUOTE=erik1397]so i have chosen "restrictive by default" with the following services allowed:
HTTP
HTTPS
FTP
SAMBA
AOL IM
MSN IM
DHCP
all of these are set to "when the source is: anyone"
does all of this sound good and safe?  do I need to open some other ports that are important/essential/common?

btw, i use ftp just to upload files to my website, and to upload files to ubuntuforums (like screenshots) i guess;
i use samba for my local network with windows pc's;
my network is DHCP[/QUOTE]
no ... that means  you are allowing ftp access to your machine from the internet side.  you need to allow those ports (apart from aol and msn) only for the network side.  especially for ftp.

---

### Post by nanotube on 2006-05-29
i find firestarter to be kind of a pain to use. i prefer using iptables directly. if you want to see my simple firewall config, check out the first link in my sig, and go to the firewall section. :)

---

### Post by user1397 on 2006-06-20
okay i'm back after a long time to configure my firewall once in for all.  I'll give you guys all that I use, the reasons why I use them, and then please tell me where to allow these services in firestarter, and if I should allow it for everyone, or just my computer's IP, or what.

( I'm guessing for all of these, I have pretty much no idea what i'm doing, so please correct me if i'm wrong. )

NTP - isn't this for ubuntu to synchronize with the time servers?
HTTP - web browsing
HTTPS - secure web browsing
FTP - downloading stuff from sites (like ubuntu images)
SAMBA - i don't have a shared folder on my ubuntu box, but I have a network with 3 other windows boxes that I backup my ubuntu files on.  For more info on what my network looks like, check out my attachment.
AOL IM - instant messaging
MSN IM - instant messaging
BITTORRENT - downloading bittorrent files (like ubuntu images)
DHCP - my network is DHCP

EDIT: Also, i've heard that if I don't run a web server, samba server, or a mail server, and if my compuer is not being used as a gateway for a network, i don't need a firewall.  I don't really know if I'm running a samba server or if my computer is being used as a gateway for a network.  How can I tell?

---

### Post by user1397 on 2006-06-20
anyone? :(

---

### Post by user1397 on 2006-06-20
man these things go down fast!  anyway, I just wnanted to say that i'm so confused!  i really want to mae use of this firewall, so please don't suggest configuring iptables directly.

---

### Post by nanotube on 2006-06-20
well... i don't know the specifics of samba ports, so will leave it for someone else...
but for everything else with the exception of bittorrent, you are just the client, NOT the server, so you don't need to allow any of that to come in. all you need to do is to say "allow anything out" and then to allow "all established connections in", and you are set.

for bittorrent, you would also need to enable incoming connections on whatever port you configure bittorrent to use. 

also, since according to your network architecture drawing (nice :) ), you are behind a NAT router box, and your computer is a desktop (so it's not going anywhere), your need for a firewall directly on your box is basically nil. 

just let the router forward the bittorrent port to your comp if you want bt to work well, and that's all you need.

---

### Post by user1397 on 2006-06-24
[quote=nanotube]well... i don't know the specifics of samba ports, so will leave it for someone else...
but for everything else with the exception of bittorrent, you are just the client, NOT the server, so you don't need to allow any of that to come in. all you need to do is to say "allow anything out" and then to allow "all established connections in", and you are set.

for bittorrent, you would also need to enable incoming connections on whatever port you configure bittorrent to use. 

also, since according to your network architecture drawing (nice :) ), you are behind a NAT router box, and your computer is a desktop (so it's not going anywhere), your need for a firewall directly on your box is basically nil. 

just let the router forward the bittorrent port to your comp if you want it to work well, and that's all you need.[/quote]so where exactly do I "allow anything out" and "allow all established connections"?

Below I have 3 attachments that are pictures of firestarter.  Please tell me where I have to put what, as in "allow anything out" and "allow all established connections" ?  (tell me in terms of picture a, b, or c please, so as to avoid confusion.)

also, bittorrent works fine for me, even though i don't tell my router to port-forward anything (i dont even know how!)

---

### Post by nanotube on 2006-06-25
[QUOTE=erik1397]so where exactly do I "allow anything out" and "allow all established connections"?

Below I have 3 attachments that are pictures of firestarter.  Please tell me where I have to put what, as in "allow anything out" and "allow all established connections" ?  (tell me in terms of picture a, b, or c please, so as to avoid confusion.)

also, bittorrent works fine for me, even though i don't tell my router to port-forward anything (i dont even know how!)[/QUOTE]

well, i haven't actually used firestarter myself, since i use iptables directly. but i'm guessing that doing outbound policy of "permissive by default" makes it allow anything out, and leaving the inbound policy blank, as you have it, makes it only allow established connections in, but not any new connections. but you can see if anyone specifically versed in firestarter can confirm or deny this. :)

---

### Post by falcon15500 on 2006-06-25
A quick **cat /etc/services** will give you common ports/port names.

falc

---

### Post by user1397 on 2006-06-25
[quote=falcon15500]A quick **cat /etc/services** will give you common ports/port names.

falc[/quote]thanks! that makes things so much clearer for me now...

---

### Post by Thiesen on 2006-06-25
do not forget to check the king of portforwarding out: [www.portforward.com](www.portforward.com)

---

### Post by user1397 on 2006-06-25
wait, do I even really need a configured firewall?  isn't linux safe enough as is? i'm behind a router anyway, even though i haven't configured that either! (am i supposed to?)

---

### Post by user1397 on 2006-06-26
bump!

---

### Post by user1397 on 2006-06-28
bump! (srry...)

---

### Post by ProjectGod on 2006-06-28
bump

didn't you know? nothing's safe. 

[SIZE="1"][COLOR="Silver"]nothing is sacred... especially when no one is safe... nothing is safe when nothing is sacred... :-\" [/COLOR][/SIZE]

---

### Post by user1397 on 2006-07-05
i believe this is the one topic i have never solved...:(

---

### Post by nanotube on 2006-07-05
[QUOTE=erik1397]i believe this is the one topic i have never solved...:([/QUOTE]
to decide if a firewall is necessary, read this thread (a sticky from the security subforum) [http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)

---

### Post by user1397 on 2006-07-05
[quote=nanotube]to decide if a firewall is necessary, read this thread (a sticky from the security subforum) [http://ubuntuforums.org/showthread.php?t=131616]("http://ubuntuforums.org/showthread.php?t=131616")[/quote]okay well reading that, i guess it would be kind-of idiotic to have a restrictive firewall.  so to hell with it ;)

---

