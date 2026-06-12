---
title: "stupid question but i'm asking it anyway .."
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-09-27
is it possible that an ISP could not actually be compatible with someone running Linux (notably me ..) ????

I know it sounds ridiculous, but ever since i've been on Linux full time, in the last couple of months, i've had more problems with my internet connection than I have in 2 years previously using Windows.

I'm just wondering aloud if the bandwith used by Linux, or whatever the access to the connection is, is essentially 'frowned upon' by my ISP and this is why i've had so many problems.

as an example, i've just been online perfectly normally and did nothing more than click "send" to post a reply in a forum and the connection completely hung.

I've spent the past half an hour resetting, rebooting and resetting some more, over and over again until I could connect to my ethernet modem and perform a factory reset - again - so I could get back online.

i can't really afford to go to another ISP since this one (talktalk for those in the UK) gives you the broadband for 'free', so I don't want to find out that ultimately I have to return to windows because i'm 100% linux all the way now and wouldn't go back to windows unless there was no other way, and my leg was hanging off :)

again, i know it sounds daft to ask, but maybe it will make sense to someone, or someone will be able to understand where i'm coming from.

Thanks :D

---

### Post by gshockxc on 2007-09-27
It's not a stupid question.  I'm not even running linux and I know what you mean.  I had a similar experience, completely coincidental with a change I made on the machine.  In my case, it was a physical connection (that wasn't secure) for the internet cable at the junction box where the cable enters the building.  I know it's odd, and a long shot, but it's worth a look.

---

### Post by Jussi Kukkonen on 2007-09-27
> I've spent the past half an hour resetting, rebooting and resetting some more, over and over again until I could connect to my ethernet modem and perform a factory reset - again - so I could get back online.


If you have problems connecting to your router/modem, then the problem is not the ISP.

---

### Post by Terl on 2007-09-27
There must be something else amiss.  Unless they use propietary software to connect (some dial-up guys do this) you should be able to connect whether you have Linux or Windows.

I too have had issues with connections in the house; once the cable folks had to come and redo a bunch of stuff.  They check for leaks.  I have had problems in a different house where a tree branh would rub on the cable wire outside and mess with the connections.  It would work sometimes and hassle me on others.

I have also had modems go out as well.

---

### Post by creedog on 2007-09-27
TCP/IP is TCP/IP, it should not matter what OS you are using. Most ISPs frown upon LINUX because they have no idea how to troubleshoot anything within it, however if you are using LINUX then you should not really need there assistance, OS, wise.

Are you connecting to your ISP via a router. My setup is modem connected to router, and then hosts connect to router. I figure that most people are using this setup and I doubt that any ISPs connection software is compatable with linux.

Now if you are using the setup above and you cannot get the modem to connect its the ISPs issue.
if you cannot get the router to connect, and you have verified that all settings are correct in your connect string, then its probably the isps issue as well. 
Beyond that its your issue.

Why don;t you describe your setup.

---

### Post by jasonwatkins on 2007-09-27
ok, to take you back :D

I first of all had a sagem fast 800 usb modem.  i used a guide i found in these very forums to set it up and get it running, which it did - no problems at all.

and after a few weeks of using it, it died on it's ****.  i backed up my PC and reformatted back to Vista assuming I could fix the problem from there, since I had had the modem working on Vista as well and assumed it would just connect straight back up.

No luck - whatever I did, the modem wouldn't work.  I rang the ISP support line and was told the modem wasn't compatible with Vista anyway, and oh yes, they didn't actually support Linux either - not in the sense of blocking anyone that uses it, but more in the technical support/problem fixing sense.

So they told me they'd send me a wired ethernet modem, which they did and this is what i'm using now.

i've now got a smartax mt882 wired modem with this spec ..

> COMPATIBLE WITH THE NEW WINDOWS VISTA, PC AND MAC
Small and Smart, plug and play, stable, easy set-up wizard, remote management
ADSL2+ Downstream rate of 26 Mbps, upstream rate of 1M bps,
1483B bridging and routing function, DHCP server, NAT/NAPT, PAP/CHAP, IP Filter, Firewall, protocol block, Built-in PPPOE/PPPOA dialing
MT882 gives full consideration to the household arrangements, enabling horizontal and vertical positions as well as hanging on the wall.
Technical Details
Standarts: ITU G.992.1 (G.dmt), ITU G.992.2 (G.lite), ITU G.994.1 (G.hs),
WAN: One RJ-11 port for ADSL; LAN: One USB port for USB cable & One RJ-45 port for 10/100 Base-T Ethernet
LED Indicators Power, ADSL Link , ADSL ACT, LAN Link ,USB
Operating Temperature: 0°C - 40°C ( 32 - 104°F)
AC: 90~240V, power adapter: 9 V AC 1A

easy setup, i entered the ip address for the modem and entered my login details in the setup panel and away I went.

but within 24 hours, I was having niggly problems again.   I guess the only way I could determine if it is indeed the ISP and/or the operating system is to actually go back to windows for a month and see if I have the same problems.

at the moment it's working ok, but i just know that if i shutdown or reboot or something without turning the modem off, or some random combination like that, i'm going to have another half an hour of resetting and rebooting to get it going again.

---

### Post by mridkash on 2007-09-27
I have the same router as yours. Do you connect to internet by setting modem setting to 'always on'?
If yes then the link light on the router should become orange in color after startup (of modem). 
When internet is not working, check that light first, is it green or orange, if green it'll not work, the modem couldn't establish connection with ISP.

From Ubuntu, open System>Administration>Network Tools open the ping tab and type in the ip of your router (192.168.0.1 by default) and see result, if it says succesful, then you're connected to modem. if not then check the ip and default gateway setting in network manager.

If it is the link issue, then its not an OS problem, the link light should turn orange even when the PC is turned off. If it is that problem you should ask your ISP.

And all that if you have 'always on' setting on. If not, then I dont know.

There is some command in ubuntu (I can't remember) that configures pppoe. Search for that.

---

### Post by handydan918 on 2007-09-27
> 
at the moment it's working ok, but i just know that if i shutdown or reboot or something without turning the modem off, or some random combination like that, i'm going to have another half an hour of resetting and rebooting to get it going again.

creedog is right. TCP/IP is TCP/IP. if anything works with your modem/router, then anything else should. It is O/S neutral.
Some modems/routers are more stable, others need frequent resets. If you are having issues pinging your router, change out your ethernet cable. It doesn't take much to compromise a cable.

---

### Post by sailor2001 on 2007-09-27
there is a setting on the router to maintain your mac address.. it's been so long since I set one up.......but anyhow when you shutdown and your router goes off, it make take sometime for it to  recycle to a mac address. It all should be in your router configuration. Other than that, I wish I could help you more.

---

### Post by jasonwatkins on 2007-09-27
> **sailor2001 said:**
> there is a setting on the router to maintain your mac address.. it's been so long since I set one up.......but anyhow when you shutdown and your router goes off, it make take sometime for it to  recycle to a mac address. It all should be in your router configuration. Other than that, I wish I could help you more.

that's interesting to know actually - i'm pretty new to routers to be honest, even though a friend of mine has worked in networks for 20 years and could program a router in his sleep :D

i'll certainly have a look at that later on.

i haven't really done anything else to it other than enter login details, so as far as setting it to always on i wouldn't know.

at the end of the day i guess it could just be teething trouble since i'm still essentially in my linux learning curve - add in the fact it's my first router since my cable modem days, and it may well just be niggly little problems that will eventually be resolved.

i should just be more patient :lolflag:

---

