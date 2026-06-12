---
title: "First-timer trying to get online"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-04-18
Hello Everyone,

I know VERY little about computers.  I want to learn Linux for the same reason I buy AMD and not Intel.  I took the plunge and jumped in with both feet and installed a 300GB HD on my computer, partitioned it 200/100, and loaded Windows XP Pro in first partition with Ubuntu 5.10 in the second.  It took me three days by trial and error to get that far.  I’m going to give this computer to my children and buy a 64-bit soon.  I want them both to be set up similar.  

I haven’t figured out how to get online so far.  I’ve been trying to use the Evolution installation wizard, but I don’t know how to answer some of the questions.  The drop-down options does not match the properties listed in my Windows program.  Specifically, I don’t know which option to choose for Server Type, Server Configuration, or Authentication Type.  There may be others once I get thru those.

Am I going about this right to get online, or what?  The searches that I have done in here seem to be more involved in other/additional programs, proxies, etc.  Would appreciate some help.  Thanks

---

### Post by TrojanSkin on 2006-04-18
I can't offer any advice, as I can't get online yet, either! (This is an XP I'm using for this). But if you're going the wireless route - don't bother unless you're a programmer or your hardware is automatically detected! I can't find any advice which makes any sense, except to wait for the Dapper (next) version which has support for my USB dongle built in. Good luck!

---

### Post by Jason_25 on 2006-04-18
Please, you don't have to be a programmer to do linux wireless networking.  You are doing a disservice to programmers everywhere by saying that.  To the OP: we can't guess your hardware specs or your internet connection type.  So how are we supposed to help you?

---

### Post by macdo on 2006-04-18
You are confusing things - Evolution is an email client, so you shouldn't/can't configure your connection with it.

Instead, go to Systems->Administration->Networking.

There should be a list of networking interfaces (with names like eth0, if you have an ethernet card).
Start by clicking on the DNS tab at the top, then in DNS servers click Add, and enter your DNS server. If you are connected to a router, that will probably be something on the lines of 192.168.0.1 - check your router documentation. If you are connected directly to the internet via a modem, then you need your ISP's DNS server address - look for the manual configuration settings in their documentation.
Go back to the Connections tab and click on your interface - Ethernet connection or Modem connection, and click Properties. Do what needs to be done there, it's all pretty evident. If you don't have a standard config, then I'll assume that you know what's not standard about it - or come back here :-)
Click on OK
Choose your connection interface again, and click on "Activate". 
Then, when your PC's done thinking, select that device as "Default Gateway Device". Click on OK - and you should be sorted. 
I *think* you need to reboot at this point - but I'm not sure, so test your connection first.
To test, ping something: in a command line, type ```
ping -c 1 66.102.7.147
```That will ping Google once, and your terminal should print out something that looks like this:
```
PING 66.102.7.147 (66.102.7.147) 56(84) bytes of data.
64 bytes from 66.102.7.147: icmp_seq=1 ttl=240 time=178 ms

--- 66.102.7.147 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 178.240/178.240/178.240/0.000 ms
```

If it does, well and good - now you need to set up Evolution.
Use the information for your email account to do that.

---

### Post by Guns90 on 2006-04-18
I appreciate your response Macdo.  What I'm about to say will probably tell you just how little I know.  I followed your instructions as far as selecting the Default Gateway device and clicking OK; however, (are you ready for this) I haven't a clue wear to find a 'command line'.  Sorry.  I rebooted and tried to 'connect to server' and it took me into some sort of wizard again.  Again, I don't have a clue of which options to select. The first thing it asks for is 'Service Type', then 'Server'.  Depending upon what I select, it asks for other info that I don't know; 'Server Configuration', 'Authentication type', etc.
The choices I am provided do not match those I can find in my Windows email accout. This is evrythiing I can tell you about my Windows email account:

Device Name:  		WAN Miniport (PPPOE)
Device Type:		PPPoE
Server Type:		PPP	
Transports:		Internet Protocol TCP/IP
Authentication:		PAP
Compression:		none
PPP multilink framing:	Off
Incoming (POP):		pop.sbcglobal.yahoo.com
Outgoing (SMTP):		smtp.sbcglobal.yahoo.com (SMTP authentication required)
Incoming mail server:	POP3
Incoming mail port #:	110
Outgoing mail port #:	25

Oh, I'm on an ASUS A7n8XE-Deluxe, AMD 2500+, Radeon 9200, 1.5 GB RAM, speedstream 5100 modem.

---

### Post by OffHand on 2006-04-18
I can't help you with your problem at this point but you should really start reading this guide while you are waiting for an expert to pop in your thread.

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)


BTW: If you need to use the command line go to Applications>Accessories>Terminal

---

### Post by macdo on 2006-04-18
Don't worry - the only stupid questions are the ones that you don't ask...

I'm assuming that you do in fact now have Internet access and you're trying to configure Evolution for email access?
The first screen is Identity - I'm sure you're fine with that :-)
Screen 2: Receiving Email
[INDENT]Server type: POP
Server: pop.sbcglobal.yahoo.com
username: yourusernamefromyahoo
Use Secure Connection: Never
Authentication Types: Password
Tick Remember Password (if you want to...)
I don't use Yahoo, so I can't be 100% positive about "Use secure connection" and "authentication types". Call it an educated guess.
[/INDENT]
Screen 3: Receiving Options
[INDENT]Three tick boxes - number one to automatically check for mail, number two to leave a copy of messages on the server, and I have no idea what number three does - leave it blank...[/INDENT] 
Screen 4: Sendng Email
[INDENT]Server type: SMTP
Server:smtp.sbcglobal.yahoo.com
Tick Server requires authentication
Use Secure Connection: Never
Type: Plain
Username: yourusernamefromyahoo
Tick Remember Password (unless you'd rather not...)[/INDENT]
Screen 5: Account Management. I'll let you work this one out - put whatever you want into the box (the default is your email addy).
Screen 6: Timezone. No prob there...
Screen 7: Done. Click Apply - and if you're lucky, the Evolution main screen will appear. 
Send a test email to yourself to see if it works...

I just hope that that is what you were actually asking - I ended up creating an Evolution account (I use Thunderbird, another email client) just to get the steps :-)

---

### Post by Topaz on 2006-04-18
When your computer loaded with ubuntu and opened with the desk top, it went through a search mode and found any and most likely everything attached to it. It would of found your connection to the internet. All you would of had to do is go and find firefox and see if it would let you do any searching. If you were able to search half the battle is won. Now you go to evolution ( the mail program ) and click on that it will now ask you for different information for setup, such as type of mail serfuce ( pop and what not ) you then have to give addresses like pop-server. mountain.pp.com. You also have to give your id you use for that service and the password. It is in the wizard that pops up and request other info you must fill out before you can uise evolution.

---

### Post by Guns90 on 2006-04-20
Macdo;  Sorry to have taken so long to respond.  Once I rebooted, I typed 'ping -c 1 66.102.7.147' and received the response 'connect: Network is unreachable'.  Therefor, concerning your asumption - no, I do not have access to the internet yet.  Any further help would be appreciated.

---

### Post by catlett on 2006-04-20
How are you getting on the internet with XP. Do you have dial up connection through a phone line? Do you have Broadband through your cable TV service? Do you have a modem to use for your service with XP? Does it have a wire or is it wireless? How did you (assuming you have) access the internet on your XP Pro system?

---

### Post by Papa-san on 2006-04-20
I am a nOOb as well, and am a computer idiot:rolleyes: 
However some links I found helpful are in my signature line, below!

---

### Post by Mustard on 2006-04-20
[QUOTE=Guns90]Macdo;  Sorry to have taken so long to respond.  Once I rebooted, I typed 'ping -c 1 66.102.7.147' and received the response 'connect: Network is unreachable'.  Therefor, concerning your asumption - no, I do not have access to the internet yet.  Any further help would be appreciated.[/QUOTE]

Please tell us what type of connection (adsl, cable, wireless, dialup) you are using and what hardware you are using to connect ( the brand and model of your ethernet card, wireless card, dhcp router, and other associated hardware where applicable).  It's pretty fundamental to solving the problem.

---

### Post by macdo on 2006-04-21
This thread is beginning to remind me of a joke...

Name and model of all involved hardware please. That's your router, your wireless card, your ethernet card, your modem, your ISP (and include the type of connection - dial-up, ADSL or cable), what version of ubuntu you're using, and so on.
The more information you give us, the more chance there'll be for us to help you!
Thanks in advance

---

### Post by Guns90 on 2006-04-21
Catlet,  I just know that when I get this worked out it's going to be because of something real stupid that I did/didn't do.  Unfortunately, it probably won't be the last time I embarass myself in public. 

I am using Windows XP right now.  I'm connected to the internet thru SBC DSL via my phone line using their wired Speedteam 5100 modem.  Whenever I boot up Ubuntu, I go directly to the desk top after I input my UserID and password.  When I click on Firefox it brings up an Ubuntu introduction screen with a url of 'file:///usr/share/ubuntu-artwork/home/index.html'.  From that screen, the only options I can find are to either minimize or X-out.

---

### Post by Guns90 on 2006-04-21
Okay Macdo, 

My Windows conection is using an OHCI Compliant IEEE 1394 net adaptor which is integrated in my ASUS A7N8XE-Deluxe motheboard.  The modem is an SBC-owned wired Speedstreem 5100 using my phoneline to connect me to SBC DSL.  I'm using Ubuntu ver. 5.10.

(Is it the joke about how many geeks does it take to get a moron online?)

---

### Post by macdo on 2006-04-21
The easiest way to get online is probably to connect your ethernet port (which looks like this [IMG]http://techpubs.sgi.com/library/dynaweb_docs/0650/SGI_EndUser/books/Fuel_UG/sgi_html/figures/A-1.Ethernet.10baseT.gif[/IMG]
to the ethernet port on your modem. Unplug the USB (or is it Firewire?) cable, and boot Ubuntu. It might well recognise it immediately. If it doesn't, type in ```
sudo ifup eth0
``` at the command line, and post results.

No, the joke has nothing to do with morons... Nobody's a moron because they don't know how to do something they've never done before. I don't know how to  switch a plane on, or repair an electrical fault.

---

### Post by Guns90 on 2006-04-21
Macdo, I have two ports.  I tried both of them in windows and there was no noticeable difference.  I also tried both ports while in Ubuntu with the following results:

Input:   sudo ifup eth0
output: password?
input:   my password
output: interface eth0 already configured

(My moron comment was an attempt at humor.  Guess I'm not very good at that either.)

---

### Post by Mustard on 2006-04-21
If we sit here chatting about how bad we are all at making jokes, at least we can hope to chew up enought time for someone  to come along that knows something about networking. :)

Here is some reading material for you to pass the time. ;)
[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

Don't hesitate to ask questions, if something confuses you, or looks like you are reading manuals written in Martian languages.

---

### Post by macdo on 2006-04-21
While your modem is connected to your PC via ethernet, could you give us the output of the command ```
ifconfig -a
```

I take it you tried but still can't connect even when connected via ethernet...
In case you were wondering, by the way, connecting via ethernet is considered to be easier than via USB. Ubuntu will normally detect the connection all by itself.

(I did get your joke, but I've often felt moronic while trying to do things on my PC...:p )

---

### Post by Guns90 on 2006-04-21
With answers like this one, maybe I ought to concentrate on either getting ubuntu to recognize my printer, or find out how to save an Office Writer document onto my floppy.  Here's what I received...

gary@ubuntu:~$ ifconf -a
eth0    Link encap:Ethernet HWaddr  00:11:2F:35:79:02
        inet6 addr: fe80::211:2fff:fe35: 7902/64 Scope: Link
        UP BROADCAST MULTICAST MTU:1500 Metric 1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txquelen:1000
        RX bytes:0 (o.o b) TX bytes:0 (0.0 b)
        Interrupt:22 Base address:0xa000

eth1    Link encap:Ethernet HWaddr  00:11:2F:32:20:1F
        inet6 addr: fe80::211:2fff:fe35: 7902/64 Scope: Link
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txquelen:1000
        RX bytes:0 (o.o b) TX bytes:0 (0.0 b)
        Interrupt:17

lo       Link encap:Local Loopback
        inet6 addr: 127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope: Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:188 errors:0 dropped:0 overruns:0 frame:0
        TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txquelen:1000
        RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
gary@ubuntu:~$

---

### Post by macdo on 2006-04-21
hmm, I'm utterly baffled. 
I just can't see why it's not working! 
I'll do some research, and get back to you...

---

### Post by daageep on 2006-04-21
i didn't read the thread really thorougly, so forgive me if you guys have already tried this solution.

from your ifconfig output, it seems your ethernet devices are eth0 and eth1. just plug the cable in any of the ports and try the following:

ifconfig eth0 up
sudo dhclient eth0

hopefully that works. =)

edit: replace eth0 with eth1 if it doesn't do anything for eth0

---

### Post by annda on 2006-04-21
Hi!

I had the same problem some time ago after substituting my old router with a DSL modem (both connected through LAN/Ethernet). I am clueless as to networking terminology and so on but I finally managed to solve the problem. I can't find the forum thread where I found the solution so I'll try to describe it in my own simple terms.

The thing is that a pure modem (as opposed to a modem/router) needs to get instructions from the computer every time you want it to establish a connection, i.e. you're not just "hooked up" by a cable to an existing network - which the eth interfaces obviously assume. You have to teach your OS how to do it. Under Windows you probably have a dialer provided by your ISP or you used a connection wizard to configure the connection. Here you have to do the same using pppoeconf. Take a look at the wiki link from Mustard for details.

Well, that did the trick for me, I hope it'll work for you too. Good luck and let us know how far you've got.

---

### Post by Guns90 on 2006-04-21
daageep,  Here's what happened...

ifconfig eth0 up
Siocsifflags: Permission denied
sudo dhclient eth0
Password:  (I entered password)
Internet SystemsConsortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved. 
For information, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:2f:35:79:02
Listening on LPF/eth0/00:11:2f:35:79:02
sending on LPF/eth0/00:11:2f:35:79:02
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
gary@ubuntu:~$

ifconfig eth1 up
Siocsifflags: Permission denied
sudo dhclient eth1
Password:  (I entered password)
Internet SystemsConsortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved. 
For information, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:11:2f:32:20:1f
Listening on LPF/eth1/00:11:2f:32:20:1f
sending on LPF/eth1/00:11:2f:35:79:02
sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
gary@ubuntu:~$

---

### Post by Guns90 on 2006-04-22
Houston, Tranquillity Base here. The Eagle has landed.

Annda, it was the 'sudo pppoeconf' followed by the 'pon dsl-provider' commands that did the trick. 

 I can't thank all of you enough for the help you provided.  I'm pretty sure this won't be the last time you hear from me.  I promise I'll try to do a little more research on topics before I give up and come groveling.  Now if you'll excuse me, I have an about a million programs to learn how to use.  Thanks again.

---

### Post by Mustard on 2006-04-22
[QUOTE=Guns90]Houston, Tranquillity Base here. The Eagle has landed.

Annda, it was the 'sudo pppoeconf' followed by the 'pon dsl-provider' commands that did the trick. 

 I can't thank all of you enough for the help you provided.  I'm pretty sure this won't be the last time you hear from me.  I promise I'll try to do a little more research on topics before I give up and come groveling.  Now if you'll excuse me, I have an about a million programs to learn how to use.  Thanks again.[/QUOTE]

Wow.  10 out of 10 for persistence. :)

I'm glad to hear that you worked it out. :D

---

