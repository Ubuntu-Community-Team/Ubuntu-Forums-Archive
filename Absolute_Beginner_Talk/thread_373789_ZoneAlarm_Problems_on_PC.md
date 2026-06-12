---
title: "ZoneAlarm Problems on PC"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by forrestguide on 2007-03-01
Hi Folks,

I'm wondering if you can solve a mystery. I'm trying to access the net, and can't with zonealarm running.  

My Win XP computer is the computer that connects to the net. If I turn off ZoneAlarm, then I can connect. Even when I have zonealarm running, but with the firewall off I can't connect, I actually have to turn off ZoneAlarm. I really like this firewall/anti-virus so I want to keep it.

I don't know how to do any manual (line editing) or what ever it's called - "what a greenhorn"!!!

If anyone is familiar with this issue please advise me.

Thanks in Advance.

Greg

---

### Post by cantormath on 2007-03-01
you know this is a linux,,,,and Zonealarm does not work on linux.

But  I will help....because that is what linux people do.......
Dont use zonealarm.  Use the built in Microsoft Firewall......you say your are on XP, XP has a built in firewall, so there is no reason for zonealarm..........and use avg(the free version or the pay-version, they both work great) for a virus scanner.  Also, Use Windows Defender, for spam and stuff.  Uninstall MCaffee, Norton, and anything else that is a virus checker, spyware program or firewall, especially spybot, adaware.....that stuff is terrible.  That setup will work very well.

---

### Post by gjtoth on 2007-03-01
> **forrestguide said:**
> Hi Folks,

I'm wondering if you can solve a mystery. I'm trying to access the net, and can't with zonealarm running.  

My Win XP computer is the computer that connects to the net. If I turn off ZoneAlarm, then I can connect. Even when I have zonealarm running, but with the firewall off I can't connect, I actually have to turn off ZoneAlarm. I really like this firewall/anti-virus so I want to keep it.

I don't know how to do any manual (line editing) or what ever it's called - "what a greenhorn"!!!

If anyone is familiar with this issue please advise me.

Thanks in Advance.

Greg

Try the ZoneAlarm forums.. I guess.

---

### Post by Tomosaur on 2007-03-01
EDIT: Actually scratch that.

If you're using some software to connect your linux and windows machine, try setting zonealarm to let that software connect to the net. You ARE trying to get to the net through the windows machine, right, or am I way off base here?

---

### Post by neogeek on 2007-03-01
Hi, 
Try the allowing Firefox to access the net ... put a check mark next to it.

---

### Post by forrestguide on 2007-03-01
Not at all!  I'm trying to figure out linux so I can use it.  That's all.  Eventually, I'd love to wean myself off of winderz. I"m sure I can do without it.

---

### Post by dr_d on 2007-03-01
zonealarm may be blocking your dns requests. i remember back in the days when i was using windows this happened to me.

here's how to find out if this is the case:

type into a terminal "ping -c 1 google.com"

if you get an ip address anywhere in the output, for example:
"PING google.com (64.233.187.99) 56(84) bytes of data."
then dns is working ok. if however, you dont get out an ip address, then it's likely that ZA is blocking your dns lookups.


I'm not sure how to fix it, but I recall that I resolved the issue by reinstalling ZA.

hope that helps:popcorn:

---

### Post by STREETURCHINE on 2007-03-01
> **cantormath said:**
> you know this is a linux,,,,and Zonealarm does not work on linux.

But  I will help....because that is what linux people do.......
Dont use zonealarm.  Use the built in Microsoft Firewall......you say your are on XP, XP has a built in firewall, so there is no reason for zonealarm..........and use avg(the free version or the pay-version, they both work great) for a virus scanner.  Also, Use Windows Defender, for spam and stuff.  Uninstall MCaffee, Norton, and anything else that is a virus checker, spyware program or firewall, especially spybot, adaware.....that stuff is terrible.  That setup will work very well.

please dont use the windows firewall,it is useless you may as well run without one...:( 

that said just uninstall zone alarm,
then reinstall it and when it starts asking you to allow programs say yes with out ticking allway allow,
when your sure the programs are safe then tick the allways allow,
if you are not sure about a program then deny it , (but dont tick the allways deny box)and see what happens if you cant acces the net then you know that it needs to be allowed.
zone alarm is a good firewall it just needs to be trained.
it has a few compatability issues but mostly it is fine

---

### Post by forrestguide on 2007-03-01
type into a terminal "ping -c 1 google.com"

if you get an ip address anywhere in the output, for example:
"PING google.com (64.233.187.99) 56(84) bytes of data."
then dns is working ok. if however, you dont get out an ip address, then it's likely that ZA is blocking your dns lookups.


Yup, good clue there.  I did this with zone alarm and nada. then with zonealarm down and bam it worked.

I guess I might have to ditch it. or reinstall.

Thanks much.

Greg

---

### Post by forrestguide on 2007-03-01
I agree ZoneAlarm is wonderful  It's caught hundreds of minor threats and 22 major ones and I'm a dial-up guy.  Imagine what would happen if I had broad band.
 
Good Advise.

Thanks

Greg

---

### Post by STREETURCHINE on 2007-03-01
i would reinstall,
then run through all your programs and allow them acces to the net,

once done it will all be good.

zone alarm is one of the best firewalls out there dont give up

---

### Post by airtonix on 2007-03-01
no sorry its not the best......it cant do nat translations which is what you need here. last time i used it it could not make rules for specific computers.

seriuosly ditch that bloatware. blackice is no better it fails to notify the user of a "hack in progress" 

For windows that best is sygate personal firewall. its simpler thatn tiny personal firewall and not gimpped to noob hell like zonealarm is.

sorry but i gotta take four thousands steps back when the fbi get personall involvment with zonealarm development.(a check on the grc.com website will reveal this)

can anyone say carnivore ? anyone? ahem i rest my case. 

trust me before i had dial up, i did the two computer thing with one being the firewall....why? coz i like being safe. and not having to cower in the corner...yeah i can walk down the street with my bodyguards so i dont have to feel intimidated by viri(or fbi/riaa/m$ employed haxors for that matter).

zone alarm doesnt do nat translation.....not like sygate and iptables/dnsmasq can. it really isnt worth the money, and sygate personal firewall is free...

but really you should be ditching that windowze and putting ubunt on...dapper i can get my modems detected using the scanmodem script available on the ubuntu wiki site.

why ditch it? so you can use on of these : 

 firestarter : a gui for the firewall already intergrated into the deep dark areas of your linux kernel
 shorewall : really easy cli for iptables....ie to allow all traffic from 10.1.1.13 [B]= $ sudo shorewall allow 10.1.1.13
[/B] guarddog : another cool gui that has more options than firestarter.

oh and you wont need application filtering like you do on windows.....since i trust all the software i install from the repos. and noen of them are nagware that will want you to give value back to the developers in the way if adverts or spyware that steals your personal details for those telemarketers dbase cds....

---

### Post by Detonate on 2007-03-01
Well, if you had broadband, you would have a built-in hardware firewall in your cable or dsl modem and you would not really need a software firewall.:)

---

### Post by STREETURCHINE on 2007-03-01
certainly would not put my trust in a router or modem firewall by itself,as they are easy to bypass,you still need a good firewall on your computer...:)

---

### Post by theonlyrealperson on 2007-03-02
> **STREETURCHINE said:**
> certainly would not put my trust in a router or modem firewall by itself,as they are easy to bypass,you still need a good firewall on your computer...:)

I agree, if your machine is always on, you need more than the hardware firewall. Windows Firewall is completely useless. You need to block uninitiated outgoing requests (malware/spyware/keyloggers calling out) as well as uninitiated incoming requests - and those two just don't do it.

Sygate, if I remember correctly, is shareware. Kerio used to make a good one, but they're gone.

Zonealarm is good, but is a huge resource hog. Comodo Firewall is a good upstart (I still have to use Win for a few things), and I highly recommend it. It's a little more sensitive than Zonealarm though, so you'll get a few more false flags.

---

### Post by SunnyRabbiera on 2007-03-02
I used to be a heavy zonealarm user when I was a doze user, a reinstall might be a good option.
as far as free firewalls go ZA is hands down the best with all the others dead or comprimised by spyware.
If you could afford it though, i rather you use Mcaffee then say norton as norton really sucks.

---

### Post by bigken on 2007-03-02
> **cantormath said:**
> you know this is a linux,,,,and Zonealarm does not work on linux.

But  I will help....because that is what linux people do.......
Dont use zonealarm.  Use the built in Microsoft Firewall......you say your are on XP, XP has a built in firewall, so there is no reason for zonealarm..........and use avg(the free version or the pay-version, they both work great) for a virus scanner.  Also, Use Windows Defender, for spam and stuff.  Uninstall MCaffee, Norton, and anything else that is a virus checker, spyware program or firewall, [SIZE=3]**especially spybot, adaware.....that stuff is terrible.**[/SIZE]  That setup will work very well.


are u sure

---

### Post by forrestguide on 2007-03-02
> **theonlyrealperson said:**
> I agree, if your machine is always on, you need more than the hardware firewall. Windows Firewall is completely useless. You need to block uninitiated outgoing requests (malware/spyware/keyloggers calling out) as well as uninitiated incoming requests - and those two just don't do it.

Sygate, if I remember correctly, is shareware. Kerio used to make a good one, but they're gone.

Zonealarm is good, but is a huge resource hog. Comodo Firewall is a good upstart (I still have to use Win for a few things), and I highly recommend it. It's a little more sensitive than Zonealarm though, so you'll get a few more false flags.
thank you for your ideas. zone alarm is still giving me problems.  I have to drop it completely to use the computer, sometimes it works if I just turn off the firewall. Maybe zonealarm's newest release is better but I"m not impressed with the performance with linux

---

### Post by STREETURCHINE on 2007-03-02
are you using zone alarm for windows or for linux

---

### Post by janz84 on 2007-03-02
> **forrestguide said:**
> I agree ZoneAlarm is wonderful  It's caught hundreds of minor threats and 22 major ones and I'm a dial-up guy.  Imagine what would happen if I had broad band.

Thousands my friend...

---

### Post by poohbear1616 on 2007-03-02
Just for grins I'll throw this in.
I have a dsl connection with a gateway/router with a built in firewall (pretty good one actually).
Now when I still used winblows if I activated a firewall in my system I had major problems, the two would conflict apparently. Never had any troubles with iptables.

---

### Post by STREETURCHINE on 2007-03-02
> **poohbear1616 said:**
> Just for grins I'll throw this in.
I have a dsl connection with a gateway/router with a built in firewall (pretty good one actually).
Now when I still used winblows if I activated a firewall in my system I had major problems, the two would conflict apparently. Never had any troubles with iptables.

yes if you are behind a hardware firewall as well you have to lower zone alarms security level to allow the network,i have zonealrm pro ,but i am currantly testing avg internet security suite , i have no problems with either of them yet,
as i said it is just a matter of training them.

---

### Post by janz84 on 2007-03-02
or you could disable "program control"

---

### Post by dr_d on 2007-03-04
well, on windows i would definitely use a software firewall as well as being behind a nat router because you never know when another 0day vulnerability is going to be discovered.

being natted will prevent against attack code that serves a shell on a local port, and the software firewall will (hopefully) prevent against reverse (connect-back) attacks.

that being said, if you manage to inject into an internet explorer process then suddenly the software firewall is useless.


now i no longer have windows, and i run ubuntu without any software firewall. i'm not even natted anymore. because my packages are authenticated and kept up-to-date, i feel safe to be connected directly to the ineternet.... if ever i do need to block off a port or do something fancy, i just use iptables -- nothing could be more powerful.

:popcorn:

---

### Post by Punker on 2007-03-30
> **cantormath said:**
> you know this is a linux,,,,and Zonealarm does not work on linux.

But  I will help....because that is what linux people do.......
Dont use zonealarm.  Use the built in Microsoft Firewall......you say your are on XP, XP has a built in firewall, so there is no reason for zonealarm..........and use avg(the free version or the pay-version, they both work great) for a virus scanner.  Also, Use Windows Defender, for spam and stuff.  Uninstall MCaffee, Norton, and anything else that is a virus checker, spyware program or firewall, especially spybot, adaware.....that stuff is terrible.  That setup will work very well.

:lolflag: I seen this  and I lost it

---

