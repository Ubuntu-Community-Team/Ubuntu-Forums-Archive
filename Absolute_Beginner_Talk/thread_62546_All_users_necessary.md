---
title: "All users necessary?"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by shnazzle on 2005-09-05
Hey,

Just had an odd question. If I go into my user/group administration window, I see there are a LOT of 'extra' users other than root and my own home login. What exactly is the function of them and can I/can I not get rid of them?

cheers

---

### Post by cwaldbieser on 2005-09-05
[QUOTE=shnazzle]Hey,

Just had an odd question. If I go into my user/group administration window, I see there are a LOT of 'extra' users other than root and my own home login. What exactly is the function of them and can I/can I not get rid of them?

cheers[/QUOTE]
Some programs that are running all the time create "users" that they run as on the system.  This way, if there is a problem or exploit with the program, it will only have permissions to mess up its own files.  Most or these users don't have a /home directory or anything like that, so keeping them around isn't eating up much disk space.  Many are necessary for your day-to-day oerations.  The name of the user should give you some indication as to what program is using it in mayn cases.  If you have questions about specific users, just ask.

---

### Post by shnazzle on 2005-09-05
Cheers for das reply. The real issue at hand for me is security. When I check my System Log  (I have discovered it! Woohoo! Under System Tools...anyway..) I can see that a lot of people try to hack into my system using brute force...daily. I figured, if I have all these other usernames...doesn't that make me more vulnerable? Can I assume that each one of the created users has been locked out of anything vital?

---

### Post by poofyhairguy on 2005-09-05
[QUOTE=shnazzle]. When I check my System Log  (I have discovered it! Woohoo! Under System Tools...anyway..) I can see that a lot of people try to hack into my system using brute force...daily. [/QUOTE]

Really?

---

### Post by shnazzle on 2005-09-05
[QUOTE=poofyhairguy]Really?[/QUOTE]

Really :)   I'm not kidding. Every day. With the exception of maybe a 1 or 2 days every few weeks. I've actually never had thsi when I ran Windows. I had the occasional attempt in my Apache server, but nothing like this.

---

### Post by rafakl on 2005-09-05
heheheheh....

but dont worry, linux is one of the safests systems in the world... BUT patch it regulary  (with sudo apt-get upgrade).....

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=shnazzle]Cheers for das reply. The real issue at hand for me is security. When I check my System Log  (I have discovered it! Woohoo! Under System Tools...anyway..) I can see that a lot of people try to hack into my system using brute force...daily. I figured, if I have all these other usernames...doesn't that make me more vulnerable? Can I assume that each one of the created users has been locked out of anything vital?[/QUOTE]
Yeah, the idea is that each of those users only has as much permission as it needs to do its job.

What makes you think someone is trying to hack your system with a brute force attack?  Have you enabled some sort of server like telnet, ftp, or ssh?  By default, Ubuntu doesn't have any servers running, so there is not really any way for someone to hack it.  

If you do have some network server running, I would reccomend you configure your firewall to block the outside traffic (at least temporarilly if possible), and alert your ISP to the situation.  The best defense in this case is to put out a big "Not Welcome!" sign.

---

### Post by shnazzle on 2005-09-06
Here isa copy paste of my system log, and this is only one example :
 
localhost sshd[17143] Invalid user a from ::ffff:82.234.26.188
localhost sshd[17145] Invalid user b from ::ffff:82.234.26.188
localhost sshd[17149] Invalid user c from ::ffff:82.234.26.188
localhost sshd[17151] Invalid user d from ::ffff:82.234.26.188
localhost sshd[17155] Invalid user e from ::ffff:82.234.26.188
localhost sshd[17157] Invalid user f from ::ffff:82.234.26.188
localhost sshd[17159] Invalid user g from ::ffff:82.234.26.188
localhost sshd[17161] Invalid user h from ::ffff:82.234.26.188
localhost sshd[17165] Invalid user i from ::ffff:82.234.26.188
localhost sshd[17167] Invalid user j from ::ffff:82.234.26.188
localhost sshd[17169] Invalid user k from ::ffff:82.234.26.188
localhost sshd[17171] Invalid user l from ::ffff:82.234.26.188
localhost sshd[17175] Invalid user m from ::ffff:82.234.26.188
localhost sshd[17177] Invalid user n from ::ffff:82.234.26.188
localhost sshd[17179] Invalid user o from ::ffff:82.234.26.188
localhost sshd[17183] Invalid user p from ::ffff:82.234.26.188
localhost sshd[17185] Invalid user q from ::ffff:82.234.26.188
localhost sshd[17187] Invalid user r from ::ffff:82.234.26.188
localhost sshd[17191] Invalid user s from ::ffff:82.234.26.188
localhost sshd[17193] Invalid user t from ::ffff:82.234.26.188
localhost sshd[17195] Invalid user u from ::ffff:82.234.26.188
localhost sshd[17197] Invalid user v from ::ffff:82.234.26.188
localhost sshd[17199] Invalid user w from ::ffff:82.234.26.188
localhost sshd[17203] Invalid user x from ::ffff:82.234.26.188
localhost sshd[17205] Invalid user y from ::ffff:82.234.26.188
localhost sshd[17209] Invalid user z from ::ffff:82.234.26.188
localhost sshd[17211] Invalid user aa from ::ffff:82.234.26.188
localhost sshd[17213] Invalid user bb from ::ffff:82.234.26.188
localhost sshd[17215] Invalid user cc from ::ffff:82.234.26.188
localhost sshd[17219] Invalid user dd from ::ffff:82.234.26.188
localhost sshd[17223] Invalid user ee from ::ffff:82.234.26.188
localhost sshd[17225] Invalid user ff from ::ffff:82.234.26.188
localhost sshd[17227] Invalid user gg from ::ffff:82.234.26.188
localhost sshd[17229] Invalid user hh from ::ffff:82.234.26.188
localhost sshd[17233] Invalid user ii from ::ffff:82.234.26.188

usually there's a list of actual proper usernames in there like webmin, root, admin, and all that good stuff. My uncle helped me trace the IP addresses and they've led us to placed from Italy, to Tokyo, to Brazil

I have a ssh and http server running, I already made a little script (that took a while to get working) that disables the servers and enables them when I want to. So thanks for the temporarily disabling tip. As for the firewall....that's 'iptables'  right?  I still have no clue how that works.

---

### Post by cwaldbieser on 2005-09-06
[QUOTE=shnazzle]Here isa copy paste of my system log, and this is only one example :
 
localhost sshd[17143] Invalid user a from ::ffff:82.234.26.188
localhost sshd[17145] Invalid user b from ::ffff:82.234.26.188
localhost sshd[17149] Invalid user c from ::ffff:82.234.26.188
localhost sshd[17151] Invalid user d from ::ffff:82.234.26.188
localhost sshd[17155] Invalid user e from ::ffff:82.234.26.188
localhost sshd[17157] Invalid user f from ::ffff:82.234.26.188
localhost sshd[17159] Invalid user g from ::ffff:82.234.26.188
localhost sshd[17161] Invalid user h from ::ffff:82.234.26.188
localhost sshd[17165] Invalid user i from ::ffff:82.234.26.188
localhost sshd[17167] Invalid user j from ::ffff:82.234.26.188
localhost sshd[17169] Invalid user k from ::ffff:82.234.26.188
localhost sshd[17171] Invalid user l from ::ffff:82.234.26.188
localhost sshd[17175] Invalid user m from ::ffff:82.234.26.188
localhost sshd[17177] Invalid user n from ::ffff:82.234.26.188
localhost sshd[17179] Invalid user o from ::ffff:82.234.26.188
localhost sshd[17183] Invalid user p from ::ffff:82.234.26.188
localhost sshd[17185] Invalid user q from ::ffff:82.234.26.188
localhost sshd[17187] Invalid user r from ::ffff:82.234.26.188
localhost sshd[17191] Invalid user s from ::ffff:82.234.26.188
localhost sshd[17193] Invalid user t from ::ffff:82.234.26.188
localhost sshd[17195] Invalid user u from ::ffff:82.234.26.188
localhost sshd[17197] Invalid user v from ::ffff:82.234.26.188
localhost sshd[17199] Invalid user w from ::ffff:82.234.26.188
localhost sshd[17203] Invalid user x from ::ffff:82.234.26.188
localhost sshd[17205] Invalid user y from ::ffff:82.234.26.188
localhost sshd[17209] Invalid user z from ::ffff:82.234.26.188
localhost sshd[17211] Invalid user aa from ::ffff:82.234.26.188
localhost sshd[17213] Invalid user bb from ::ffff:82.234.26.188
localhost sshd[17215] Invalid user cc from ::ffff:82.234.26.188
localhost sshd[17219] Invalid user dd from ::ffff:82.234.26.188
localhost sshd[17223] Invalid user ee from ::ffff:82.234.26.188
localhost sshd[17225] Invalid user ff from ::ffff:82.234.26.188
localhost sshd[17227] Invalid user gg from ::ffff:82.234.26.188
localhost sshd[17229] Invalid user hh from ::ffff:82.234.26.188
localhost sshd[17233] Invalid user ii from ::ffff:82.234.26.188

usually there's a list of actual proper usernames in there like webmin, root, admin, and all that good stuff. My uncle helped me trace the IP addresses and they've led us to placed from Italy, to Tokyo, to Brazil

I have a ssh and http server running, I already made a little script (that took a while to get working) that disables the servers and enables them when I want to. So thanks for the temporarily disabling tip. As for the firewall....that's 'iptables'  right?  I still have no clue how that works.[/QUOTE]
You can get some simple GUI front ends like firestarter to do simple firewalls.  However, that won't help you if someone has firgured out what port you are running a specific server on.  Something like this: [http://doorman.sourceforge.net/](http://doorman.sourceforge.net/) might be more useful to you.  It makes it look like you don't actually have any ports open unless you try to access them in the correct sequence.  I don't know if there is something like that in the repositories, but you could ask around.

---

### Post by shnazzle on 2005-09-07
Hmm, interesting program. But it is kind of a nuisance. Isn't there a program that monitors ssh or http logins and matches login patterns with those of typical brute force attempts and then automatically blocks that connection? That would be a bit handier, Cus with the Doorman I have to give all the people I have visit my site this program, Knocker.

I'm tinkering with Firestarter now, it seems easy enough but so far I can't get it properly configured. In Windows ZOneAlarm made my pc completely "stealth" on the net, according to the "Shields UP!" website. So far Firestarter does not accomplish this. Is there something that I am (not) doing wrong?

I'm already looking into some programming to see if I can get a project going for that brute login matching program. That would be neat...or is it completely unnecessary?

---

### Post by amohanty on 2005-09-07
If you are getting hit so badly on a regular basis I think an investment in a small true firewall like one of the low end SonicWalls would be well worth it. You have to realize that security is mostly a reactive phenomenon from the securer's point of view. You can patch your stuff regularly, maintain secure practises but at the end of the day all you can hope for is that if a smart cracker breaks in you get to know about it soon enough. In that scenario event the true firewall is nothing more than an additional obstacle but it will get you into the more favorable position of knowing asap when someone _does_ break in sooner.

AM

---

### Post by cwaldbieser on 2005-09-07
[QUOTE=shnazzle]Hmm, interesting program. But it is kind of a nuisance. Isn't there a program that monitors ssh or http logins and matches login patterns with those of typical brute force attempts and then automatically blocks that connection? That would be a bit handier, Cus with the Doorman I have to give all the people I have visit my site this program, Knocker.

I'm tinkering with Firestarter now, it seems easy enough but so far I can't get it properly configured. In Windows ZOneAlarm made my pc completely "stealth" on the net, according to the "Shields UP!" website. So far Firestarter does not accomplish this. Is there something that I am (not) doing wrong?

I'm already looking into some programming to see if I can get a project going for that brute login matching program. That would be neat...or is it completely unnecessary?[/QUOTE]

Well, if you have a public HTTP server and ssh server, you can't really be completely invisible.  If you want the firewall to block *everything*, I think the following iptables commands should drop all packets:
```

$ sudo iptables -t filter -P FORWARD DROP
$ sudo iptables -t filter -P INPUT DROP
$ sudo iptables -t filter -F

``` 
The first line sets the FORWARD chain's default policy to silently drop packets.  The second does the same thing for the INPUT chain.  The last command flushes all the existing rules out of the filter table.  This means that if a packet is destined for your server, the INPUT chain drops it.  If the packet is destined to be forwarded to some other computer, the FORWARD chain drops it.  Because there are no other rules to match, these policies are always used.

Not sure how useful this is.  What ports does the Shields Up! site tell you are giving a rejection notice?

---

### Post by adun on 2005-09-07
you get rid of most of these 'attacks' by changing your sshd port. 
furthermore a script which drop every connection from a specific IP after for example 3 bad tries (for a specific time) is usefull. (easy to write)


@topic most auf the system users are not allowed to log in, except root. thats why it is absolute recommended to prohibid a direct ssh root login.

---

