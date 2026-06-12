---
title: "Ubuntu doesn't work with Comcast"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by gsub on 2008-01-15
Hello, everyone.

I'm using Ubuntu Gutsy on my laptop, comcast is my ISP, and there's something strange going on.

I'm able to connect to the internet using a windows box, but not with ubuntu.
To add to the confusion, my ubuntu laptop connects to the web anywhere else, including a friend's comcast internet connection.

I've tried arguing with comcast that its something on their end that needs fixing, but they wont talk to me any further once I tell them im using linux.

Does anyone have any ideas? Has anyone run into this before?

Please help !!!!!

---

### Post by SunnyRabbiera on 2008-01-15
Wierd as comcast has worked for me for ages now...
how are you connecting to the net?

---

### Post by gsub on 2008-01-15
I'm connecting in the standard way, i suppose: Coaxial cable from wall to Cable modem, Ethernet cable from cable modem to PC.

---

### Post by SunnyRabbiera on 2008-01-15
alright, is your comcast modem a standard one like one that was shipped with your service or is this one you got yourself?
does your comcast modem have a name brand on it?

---

### Post by gsub on 2008-01-15
modem's standard too... came with the service... its a motorola, and i dont remember the model - can check once i get back home from work.

---

### Post by SunnyRabbiera on 2008-01-15
ah, so its like my older modem then.
No need to check for the model in that case, if you need to go to work you can come back later...
just remember to bookmark this thread as this part of the forums is kinda messy :D

---

### Post by gsub on 2008-01-15
im at work already (dont tell my boss) and the thread's already been bookmarked.

---

### Post by SunnyRabbiera on 2008-01-15
its cool, when you are done work come back...
I probably have a solution for you, I just dont know it yet :D

---

### Post by gsub on 2008-01-15
no no.. i meant i can check the forum from work... just dont tell my boss... so, fire away - i'm all ears..

---

### Post by angryfirelord on 2008-01-15
I have crappy Comcast as well, but I connect through a router, so if all else fails then that may do the trick for you.

---

### Post by gsub on 2008-01-15
So... does that mean you can't connect without a router?

---

### Post by SunnyRabbiera on 2008-01-15
> **gsub said:**
> So... does that mean you can't connect without a router?

Not in my case.
I was able to use linux for a while without a router on comcast.
I am personally suspecting it might be the ethernet card as opposed to the router and or modem.
this is why this might be better if you were at home so you can look up your specs.

---

### Post by dgray_from_dc on 2008-01-15
gsub,

Does your windows machine have any Comcast software on it?

  I have comcast, and can connect with or without a router.  I have seen cases where the initial setup is done via some kind of CD for windows and the connection won't work without it.

  You have to remember, most of the techs that come to do installs and the tech support people on the phone are contractors following instructions, they can't handle the unexpected.

---

### Post by SunnyRabbiera on 2008-01-15
> **dgray_from_dc said:**
> gsub,

Does your windows machine have any Comcast software on it?

  I have comcast, and can connect with or without a router.  I have seen cases where the initial setup is done via some kind of CD for windows and the connection won't work without it.

  You have to remember, most of the techs that come to do installs and the tech support people on the phone are contractors following instructions, they can't handle the unexpected.
Uh huh.
the installation CD for comcast wont work, if you downloaded and installed anything from the disk it might have indeed messed up something.
But really it would help if I knew his other system specs so I can see what is going on.

---

### Post by gsub on 2008-01-15
Sunny: but it doesnt seem to be my ethernet card.... i can connect to other networks quite nicely.. in fact, im on the forum from the same laptop. and besides, i can surf the 'net using a friend's comcast connection with my laptop.

dgray: I dont have a windows machine - had a friend bring his over to check. so, there's no comcast software installed.

---

### Post by gsub on 2008-01-15
what system specs do you need? im using the very same laptop to send messages to this forum

---

### Post by SunnyRabbiera on 2008-01-15
> **gsub said:**
> what system specs do you need? im using the very same laptop to send messages to this forum

well things like computer model, what brand is the Ethernet card and stuff.
The reason why I ask is that while most hardware works on windows it might not work on linux.
Remember the two are different operating systems so what works in one might not work in the other.
I eliminated the modem, so I am working my way out from there.
My next one logically is to ask is of course what is the brand of the Ethernet card, this sort of thing might matter in telling you your problem

---

### Post by Flying caveman on 2008-01-15
I have Comcast,  You may have to register your MAC address [MAC address]("http://en.wikipedia.org/wiki/MAC_address")

Every piece of network equipment has its own unique MAC address.  Instead of using the MAC adress of the modem or router,  My Comcastic connection is associated with the MAC address of a windows computer I never  use.  You may look into cloning/spoofing your MAC address with a router.

---

### Post by SunnyRabbiera on 2008-01-15
> **Flying caveman said:**
> I have Comcast,  You may have to register your MAC address [MAC address]("http://en.wikipedia.org/wiki/MAC_address")

Every piece of network equipment has its own unique MAC address.  Instead of using the MAC adress of the modem or router,  My Comcastic connection is associated with the MAC address of a windows computer I never  use.  You may look into cloning/spoofing your MAC address with a router.

yeh this would be the next one on my problem checklist.
I never had to touch that part of the setup as linux detected it right away for me, but if could very well be our friends issue.

---

### Post by dgray_from_dc on 2008-01-15
If it's a MAC address problem, other PCs shouldn't work either.  Still, it may be worth a shot.

---

### Post by gsub on 2008-01-15
dgray: thats what i figured - its the mac address of the cable modem that they called in when they did the installation, not the ethernet card.

i have a dell inspiron 1505, the ones that come with ubuntu pre-installed. it is the only OS on the system.

ifconfig -a gives:

gsub@Gallifrey:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:B9:73:D3:F2  
          inet addr:144.174.128.213  Bcast:144.174.143.255  Mask:255.255.240.0
          inet6 addr: fe80::219:b9ff:fe73:d3f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151919 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22962459 (21.8 MB)  TX bytes:2926466 (2.7 MB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3696 (3.6 KB)  TX bytes:3696 (3.6 KB)

---

### Post by SunnyRabbiera on 2008-01-15
ah, well this is a dilemma then, but its also very odd too...
I am just wondering if the issue is more from comcast then it is linux now.
by the way, nice name for your computer... gallifrey :D

now here is my next line of questioning:
does your ubuntu computer state it cannot find any connection to the internet?
or is this possibly a firefox issue?

---

### Post by gsub on 2008-01-15
doesnt seem like a firefox issue - thats what im using now. besides, i cannot ping/telnet/ssh/ftp either.

---

### Post by SunnyRabbiera on 2008-01-15
hmm...
well my main suspect now is definately comcast, if you got a dell preinstalled with linux most of the hardware in it is made for linux compatibility.
How old is your current comcast modem may i ask?

---

### Post by gsub on 2008-01-15
almost brand new - bought it less than a month ago. i think its a comcast problem too - but they wont do a thing because im using linux. is ther any way to get around it?

this router business - any advice on that front?

---

### Post by SunnyRabbiera on 2008-01-15
> **gsub said:**
> almost brand new - bought it less than a month ago. i think its a comcast problem too - but they wont do a thing because im using linux. is ther any way to get around it?

this router business - any advice on that front?

sadly no, Comcast barely supports linux... maybe I got lucky.
as for a router, if you have to buy one get a linksys as they typically work well with linux.
But there is another question I must ask you, did you get your modem registered?
When I had to swap my modem out for a new one I had a hell of a time getting my modem registered with comcast.
Is this the only computer you used this modem on?

---

### Post by gsub on 2008-01-15
yes, they called in the mac address of the modem when they came by to install. this is not the only pc used with the modem - i used the windows pc to check my connection.

when i called comcast, they claim they are not at fault, as they can restart my modem remotely.

i am tempted to think that comcast is blocking access to the internet if one is using linux, but that doesnt explain why my PC works with other comcast connections.

---

### Post by SunnyRabbiera on 2008-01-15
> **gsub said:**
> yes, they called in the mac address of the modem when they came by to install. this is not the only pc used with the modem - i used the windows pc to check my connection.

when i called comcast, they claim they are not at fault, as they can restart my modem remotely.

i am tempted to think that comcast is blocking access to the internet if one is using linux, but that doesnt explain why my PC works with other comcast connections.


but your last theory makes no sense as I would not be able to use comcast either.
did you try a reboot on your ubuntu computer and try to plug the modem out then back in again to reset the net.

---

### Post by gsub on 2008-01-15
i know it doesnt - thats why i said 'im tempted to think'...

re restarting the modem/pc - i did all that..... still disconnected from the world.

:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by SunnyRabbiera on 2008-01-15
> **gsub said:**
> i know it doesnt - thats why i said 'im tempted to think'...

re restarting the modem/pc - i did all that..... still disconnected from the world.

:confused::confused::confused::confused::confused::confused::confused::confused:

wow, its got me too....
this is odd, very very odd...

---

### Post by gsub on 2008-01-15
<bump>

---

### Post by SunnyRabbiera on 2008-01-15
well for now the best I can suggest is see if you can invest in a router, or possibly another non comcast issue modem.
you can get another modem for your service, as long as you inform comcast.

---

### Post by gsub on 2008-01-15
well.. i went to the local comcast office... they say "linux? sorry... no one here knows how to troubleshoot it"

so, bought a router, and the 'net works at home <grumble> <grumble>

---

### Post by SunnyRabbiera on 2008-01-16
yeh, wierd...
but it works now right?

---

### Post by angryfirelord on 2008-01-16
> **gsub said:**
> well.. i went to the local comcast office... they say "linux? sorry... no one here knows how to troubleshoot it"

so, bought a router, and the 'net works at home <grumble> <grumble>
Look at it this way, at least now you can host some LAN parties. :)

---

### Post by AugieWest on 2008-01-16
My Comcast account requires my MAC be "provisioned." (A MAC is a unique ID for a Ethernet card,) My Linksys cable router has cloned my MAC, so Comcast thinks my MAC hasn't changed in years. All traffic to the Internet appears to come from this one MAC.

Are you using a cable router? Or just moving the Ethernet connection to the Ubuntu box? The latter probably won't work.

---

### Post by macogw on 2008-01-16
I have Comcast, and the way their modems work does involve a MAC Address handshake.  I called up and asked.  The person didn't know the word, but they called it a "handshake" and you need to power-cycle the modem (unplug for 15 seconds, plug back in) and reboot the computer to get it to do a new "handshake."  Until you do that, it won't talk to any other computer than the one with which it last did a "handshake."  Yeah, it's definitely looking at MAC Address.  If you have more than one comp and want them both to work with it, definitely get a router.  It'll have to handshake with the router, but then you can plug whatever you want into the router and be fine.  That's why I don't use my laptop at my mom's house.  She has Comcast and no router, and I don't want to go through the power-cycling stuff over and over  (I *have* had it work though when I did go through that little song & dance).  My dad has Comcast with a router, and it's fine.

---

### Post by stchman on 2008-01-16
My recommendation is to get a decent wireless router.  I have the Linksys WRT54G and it works fine with my cable modem (Charter).  The router can be had for about $50 and the wireless portion supports WEP/WPA/WPA2.  You probably have a Motorola Surfboard style modem.

---

### Post by gsub on 2008-01-16
Well.. my problem's solved, but purely out of academic interest, here's the replies to the queries (in reverse order of asking):

stchman: i bought the exact same router, and yes, i have a surfboard modem.

macogw: I'm not sure if that's the protocol these days: I took my Ubuntu box to a friend's house, disconnected her laptop from the modem and plugged mine into the modem - all this without any power cycling, and was able to connect to the 'net.

Augiewest: It seems like the MAC address of the cable modem is what matters. you can plug whatever you want (within the limits of reason, of course) into the modem (see above). Yes, I am using a cable router (wall -> cable modem -> cable router -> my PC). I'm not sure what you mean by "moving the ethernet connection to the ubuntu box".

Thanks for all the input, folks.

---

### Post by rustybronco on 2008-02-25
A little added info...
comcast ties the mac address of device they hook the ethernet/usb cable to, coming from the cable/telephony modem,  (the mac of that device is stored in the cable modem). so if you were to add a wireless router inline to the original install ( cable modem>wireless router>p.c. ) you will have to clone the mac address of that device and use it for the "new" mac address of the router. 

example of a  how-to on changing the mac address. [http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=1040&p_created=1086911813&p_sid=btIGUT4i&p_accessibility=0&p_lva=557&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTAmcF9jYXRzPSZwX3B2PSZwX2N2PSZwX](http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=1040&p_created=1086911813&p_sid=btIGUT4i&p_accessibility=0&p_lva=557&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPTAmcF9jYXRzPSZwX3B2PSZwX2N2PSZwX)

if the cable modem uses the same address  the "wireless" router uses, it would be advisable to change it from the default (my cable modem used 192.168.1.1 the same as my router ) to something like 192.168.2.1 (or 10.xx.xx.xx.xx ) so you  may not have a problem accessing the "wireless" router through your browser. 

***note*** i changed the mac address of the card in my wifes xp machine, just so if there was a problem using both the same mac addresses in the router and computer, I would not be trouble shooting that problem also. it shouldn't make a difference  but just in case I did it anyway.

if you have a problem with this method check  for a possible issue that was solved by a firmware update (my netgear wgr614-v6 needed to be updated )
 
don't forget to use the comcast supplied DNS address, or your chosen DNS server address, or you will find your ping times about 4,000 -5,000 ms  by it going in circles within comcast.


AND if you find you internet drops out after 20-30 minutes, don't overlook the obvious... make sure the power to the cable modem is not hooked to a power strip used to shut down the computer that the mac it is tied to. (ask me how I know...turned it back on a it would work again for a while, huh don't know what the problem could be??? a day later after the cable modem had no lights lit (battery back-up), DUH... )

---

