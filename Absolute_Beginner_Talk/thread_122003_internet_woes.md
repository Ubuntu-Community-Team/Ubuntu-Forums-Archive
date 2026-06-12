---
title: "internet woes"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by firefly123 on 2006-01-26
Hi
Have been trying to connect to the internet via a Globespan usb modem, had found driver, and rp-pppoe with no go as icant even starf rp-pppoe, 

SO im trying a modem router pluged into a ethernet socket on my lap top, have tried to configure with no luck, Im a newbie so HELP, Im getting info from my isp

---

### Post by bscbrit on 2006-01-26
What model of ethernet router have you got?

Essentially, you must first configure your ethernet card in the computer.  it must also be told where to find the gateway to the internet i.e. the IP address of the router.  The modem/router must also be connected to your ISP - I am assuming that you are broadband, but you could just as easily be using a dial-up if your modem/router is a fairly old model.

More information please, and I will try to help.

---

### Post by firefly123 on 2006-01-26
linksysWAG354G which is both wired and wireless, im using a etherent cable

---

### Post by bscbrit on 2006-01-26
Ok, the manufacturer's manual should tell you how to configure the modem.  It will either have a fixed IP or be functioning as a DHCP server.

Have you configured your network interface in your laptop?  Once we know which network the modem/router is operating on, we can configure your laptop onto the same network. 

I do not know how to connect your particular modem to your ISP. Again, the manual should explain it and, usually, it is a very simple and straightforward procedure.  Have you set up your modem? are you happy that it is working properly?

---

### Post by firefly123 on 2006-01-26
I have connected the modem and get all lights on,
In ubuntu i have ethernet enabled

---

### Post by bscbrit on 2006-01-26
I've downloaded the manual for your router and the default IP is 192.168.1.1    If you haven't changed it that should be OK.

---

### Post by firefly123 on 2006-01-26
Have pinged 192.168.1.1 that works

---

### Post by bscbrit on 2006-01-26
OK - you have proven that your laptop is correctly configured, that your cables are working and that you have found your modem/router.  The only problem now seems to be the configuration of your modem router.  That is not really an Ubuntu question and not something that I am qualified to advise on.

But I have downloaded your manual and can give it a try.  Have you configured your modem with the information provided by your ISP?  Is the modem giving the correct indications?  Have you accessed the web setup page on your router?

---

### Post by firefly123 on 2006-01-26
isp will not give me the info..............aol.com
when i type in 192.168.1.1 nothing happens, do i have to have the set up disk in ????

---

### Post by firefly123 on 2006-01-26
isp will not give me the info..............aol.com
when i type in 192.168.1.1 nothing happens, do i have to have the set up disk in ????

---

### Post by bscbrit on 2006-01-26
I assume that they have given you a Windows set up disk?  Do you have a dual-boot system so that you can set it up on windows, note the settings, and transfer them to Ubuntu?

I think that, in your position, I would have very stern words to say to my ISP.  They can dictate what service they provide but they shouldn't dictate which operating system you have to use.

---

### Post by bscbrit on 2006-01-26
When you say that you have typed in '192.168.1.1' - where exactly?  Have you typed it into the address field of your firefox browser?

---

### Post by mips on 2006-01-26
firefly123,

Are you using AOL in the USA or UK ???

---

### Post by firefly123 on 2006-01-26
aol in the uk, typed http//192.168.1.1 in to ie in xp no go,
im going to work thro the wired network document from hardware forum, will get back to you all later or tommorow

speak to you all soon

yours david

---

### Post by mips on 2006-01-26
I'm going to assume you are in the UK.

**_Router Config:_**
With your manual you need to setup the authentication and WAN interface.

Encapsulation Type=PPPoA with VC Mux or PPPoE with LLC Based
VPI=0
VCI=38
VPI/VCI=0,38  (Incase the format differs)
MTU=1400 (Configure MTU on Router & PC!!!)
Create a new aol screen name for your router.
Username= [email]userid@aol.com[/email] or [email]useride@aol.co.uk[/email] or whatever the domain is.
Pasword= password (max 8 chars, must be alphanumeric, must be lowercase)
Authentication=Auto
Automatic reconnect:Yes

---

### Post by bscbrit on 2006-01-26
OK, but I do not think that the problem is with your wired network.  You have good connectivity between your computer and your modem/router.  What you have not got is access to the outside world.

Check that you have entered the 192.168.1.1 address in your gateway parameter under the System -> Admin -> Networking -> eth0(or whatever you are using).  Otherwise, we will see you tomorrow.

---

### Post by mips on 2006-01-26
To change your MTU values on the PC you ahve to edit your **/etc/network/interfaces** file and add the line mtu 1400 under the interface.

Example:
```
# The primary network interface
iface eth0 inet static
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1
**[COLOR="Red"]mtu 1400[/COLOR]**
```

On the router it is simply a field where you change the value to 1400.

As bscbrit mentioned you are fine so far but I think you need to configure your WAG54G router.

---

### Post by ijwilliams1975 on 2006-01-26
have you used the internet with this router befer without problems?
if so then it sounds like you need to access the routers admin page and change some settings. I have a similar setup on ubuntu so hopefully I can help you by sending you my setup info.

Do you know the IP address of your router? (try typing [http://192.168.1.1/](http://192.168.1.1/)) into your  web browser - this is the factory default for the router. if you get a router  admin screen then your pc is connecting to the router, meaning its a router configuration issue.
If you get a connection refused error then the problem could be with a few ubuntu network settings...let me know what happens and i will try to talk you through the troubleshooting side of things!
and do you know if Ubuntu is configured for DHCP? - Automatically configure its networking from the router?

All the best,
Ian

---

### Post by mips on 2006-01-26
Lol, just found this [http://www.aol.co.uk/products/broadband/features/networking_faqs.adp](http://www.aol.co.uk/products/broadband/features/networking_faqs.adp)

AOL UK tells you how to configure your router, same as previous post above though.

---

### Post by mips on 2006-01-26
[QUOTE=ijwilliams1975]have you used the internet with this router befer without problems?
if so then it sounds like you need to access the routers admin page and change some settings. I have a similar setup on ubuntu so hopefully I can help you by sending you my setup info.

Do you know the IP address of your router? (try typing [http://192.168.1.1/](http://192.168.1.1/)) into your  web browser - this is the factory default for the router. if you get a router  admin screen then your pc is connecting to the router, meaning its a router configuration issue.
If you get a connection refused error then the problem could be with a few ubuntu network settings...let me know what happens and i will try to talk you through the troubleshooting side of things!
and do you know if Ubuntu is configured for DHCP? - Automatically configure its networking from the router?

All the best,
Ian[/QUOTE]

Looks he can ping the router so he should be fine once he configure the WAN & Authentication on the router.

---

### Post by firefly123 on 2006-01-28
Hi all

have come to a standstill as aol silver cant use a router, BUM i think this is to make people upgrade to Gold BUT as i live in the sticks in northumberland i cant get the speed for Gold, so im looking for another provider who will give me 512 speed and allow me to use a router

---

### Post by gooner on 2006-01-28
In regards to the usb modem have you tried using **eciadsl** to get it working? Because I'm also on AOL in the UK but use a BT Voyager 105 usb modem and it works perfectly. You can find it here [http://eciadsl.flashtux.org/index.php?lang=en](http://eciadsl.flashtux.org/index.php?lang=en). 
good luck

---

### Post by Inkyskin on 2006-01-28
Ditto, worked great for me too (Not AOL though)

---

### Post by firefly123 on 2006-01-29
Hi
Where can i find the settings for aol silver to place in to eclids config box
Aol are not being helpfull,I can manage to contact the aol sheffield hub then authacanthion fails
Yours david

---

### Post by gooner on 2006-01-29
Here are the settings that work for me.

User = your [email]username@aol.com[/email]
password = I'll let you figure that out for yourself
VPI = 0
VCI = 38
Update provider DNS = other
DNS 1 = aol.co.uk
DNS 2 = aol.com
Check the box that says Use DHCP
PPP Mode should be set to VCM_RF2364

Modem and synch bin options vary from modem to modem so go to the eciadsl website and find out which work best with your's.

Let us know if you need any more help. Good luck

---

### Post by firefly123 on 2006-01-29
It works but cannot get any web pages to load or load files, the data light blinks but not so much as in XP.
The last line of the output "Waiting for ppp0... " before i get the promt again signify anything, is it worth me trying diffrent bins??????

Excelent help cheers and continue the good work

avid@dg2:~$ sudo eciadsl-start | tee log.txt

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 2
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <magic 0xa4d26f11>]
sent [LCP ConfReq id=0x1 <magic 0xa4d26f11>]
rcvd [LCP ConfAck id=0x1 <magic 0xa4d26f11>]
rcvd [LCP ConfReq id=0x72 <auth chap MD5> <magic 0x261562ea>]
sent [LCP ConfAck id=0x72 <auth chap MD5> <magic 0x261562ea>]
rcvd [CHAP Challenge id=0xfd <f09e2d21574814852e06f76d786582b6>, name = "ERX14.Sheffield2"]
sent [CHAP Response id=0xfd <855fdb48cf28883e315f109a308aa0f2>, name = "grundfirefly@aol.com"]
rcvd [CHAP Challenge id=0xfe <122bbd07e6cbf2c5380fe84ea3fb758e>, name = "ERX14.Sheffield2"]
sent [CHAP Response id=0xfe <d30c3c8fdac363342fff874048a85396>, name = "grundfirefly@aol.com"]
rcvd [CHAP Challenge id=0xff <5e7a8c1d0a06dfa7fe05984a8e46dd81>, name = "ERX14.Sheffield2"]
sent [CHAP Response id=0xff <459a15d235d688a6c51594efa40adc48>, name = "grundfirefly@aol.com"]
rcvd [LCP ConfReq id=0x1 <mru 1450> <asyncmap 0x0> <auth chap MD5> <magic 0xb8bd7>]
sent [LCP ConfReq id=0x2 <magic 0xa704ac65>]
sent [LCP ConfRej id=0x1 <asyncmap 0x0>]
rcvd [LCP ConfAck id=0x2 <magic 0xa704ac65>]
rcvd [LCP ConfReq id=0x2 <mru 1450> <auth chap MD5> <magic 0xb8bd7>]
sent [LCP ConfAck id=0x2 <mru 1450> <auth chap MD5> <magic 0xb8bd7>]
rcvd [CHAP Challenge id=0x3 <4b16b7ee0ce13ec0d21b688df51e6507e1ff390add0e35c62beba91b410a2b82>, name = "ipt-lostc03"]
sent [CHAP Response id=0x3 <0a6074c2850e1af4e6cc3ed2708241e9>, name = "grundfirefly@aol.com"]
rcvd [CHAP Success id=0x3 ""]
CHAP authentication succeeded
sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [IPCP ConfReq id=0x4 <addr 81.145.241.135>]
sent [IPCP ConfAck id=0x4 <addr 81.145.241.135>]
rcvd [IPCP ConfRej id=0x1 <ms-dns3 0.0.0.0>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 172.214.114.53> <ms-dns1 205.188.146.145>]
sent [IPCP ConfReq id=0x3 <addr 172.214.114.53> <ms-dns1 205.188.146.145>]
rcvd [IPCP ConfAck id=0x3 <addr 172.214.114.53> <ms-dns1 205.188.146.145>]
not replacing default route to eth0 [192.168.1.1]
local  IP address 172.214.114.53
remote IP address 81.145.241.135
primary   DNS address 205.188.146.145
Connection successful

[EciAdsl 5/5] Setting up route table...

Waiting for ppp0...

---

### Post by gooner on 2006-01-29
OK, try this; open the file /etc/resolve.conf and check whever or not your DNS is visable. In other words it should look something like this 

nameserver 205.188.146.145

If not change it to the above (exactly the same). 

And then hopefully everything should work fine.

---

### Post by firefly123 on 2006-01-29
Hi
resolve.conf , have added line and same situation as regards the connection

nameserver aol.co.uk
nameserver aol.com
nameserver 205.188.146.145

---

### Post by gooner on 2006-01-29
Delete the first two lines and just leave it with the last (nameserver 205.188.146.145).

---

### Post by firefly123 on 2006-01-30
hi left one line in and still no go

---

### Post by gooner on 2006-01-30
Well if the one line left is "nameserver 205.188.146.145" and its still not working im not sure what else i can say. Mine works perfectly well, all i have to do after a fresh install of ubuntu is install build-essentials and the gcc lib and it works fine.

I've just noticed something in the output of eciadsl, theres a line that says "not replacing default route to eth0 [192.168.1.1]" perhaps you've misconfigured something while trying to setup the router.  I'm 100%  sure your computers connected to the net but why you cant view any webpages is beyond me. im a noob myself.

---

### Post by firefly123 on 2006-02-01
hi
got on to net, noticed line that said that there may be a file conflict with etc/ppp/options file so i renamed it aud no probs.

The only way i can connect is with the terminal command  eclids-doctor !!!!!!
any sujestions??????? as command will not work in a launcher

---

### Post by dogface2006 on 2006-02-01
In order for you to connect and browse the Internet you need to obtain the DNS ip from your ISP.
Next you can set that into your /etc/resolv.conf  just do sudo gedit /etc/resolv.conf
then SAVE
you can check connectivity with the Internet tools, try pinging Google.com using their ip 72.14.207.99
Good Luck

---

### Post by firefly123 on 2006-02-01
Can connect and browse, just looking for a 1 click method of stasting the conection

ps Browsing in ubuntu is soooooo fast, faster than xp/ie

---

