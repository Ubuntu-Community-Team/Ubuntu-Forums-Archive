---
title: "damn wireless....i have a problem"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by Tadhg on 2005-11-05
just got a new belkin PCMCIA wireless card to use with my linux laptop, problem, is the cd that comes with card is bascailly only for windows. I cant use ndiswrapper to install drivers as there are no .inf's on the cd, only exe's and sys's. Is there any drivers i can find on the net that i can use to at least get the card installed?

edit;by doing some googling, it looks like its a broadcom chipset. *off to find bw____.inf's*

---

### Post by toorima on 2005-11-05
Or you could unzip the .exe file and use the .nfo

---

### Post by Tadhg on 2005-11-05
hang on a sec. Any files on the cd are under the name rt2500 which would lead me to believe that its is a rt2500 chipset which has a nice howto [here]("https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo/") which i followed, and yet, my card is still dead. No lights, not being picked up on ifconfig.whats going on.

---

### Post by bootleg on 2005-11-05
belkin PCMCIA? 

Which model?

---

### Post by Tadhg on 2005-11-06
yea, its  a F5D7010. As i was saying, i think its a rt2500 chipset as thats what diriver comes on the cd.

First things first though, i can't even get the thing to power up. The two led's haven't been on at all. Any ideas why? I went through the tutorial here for setting it up, and the laptop thought it had a card installed (ra0) but the card wasn't even blinking.

---

### Post by TimelessRogue on 2005-11-06
Firstly, don't get in flumux about the leds not lighting up ... my Linksys leds lit briefly right after I got the card but haven't since then, even when I was using Windoze, and the card functions just fine.  Apparently your system is finding your card so the problem is probably elsewhere.

Secondly, you can extract the drivers from the .exe file on the cd and use ndiswrapper to set things up ... although I didn't have great success with this method with my card.  What I finally resorted to, since mine was a fresh install anyway and there was nothing to lose, was reinstalled Breezy with my wireless card inserted while at a wifi location ... lo and behold, all was well in wifi-land.

Also, there's another thread going: [http://www.ubuntuforums.org/showthread.php?t=86221](http://www.ubuntuforums.org/showthread.php?t=86221)  regarding a Belkin f5d7001uk card and ndiswrapper ... you might want to check that if you haven't already.

Whichever works, good luck ...

---

### Post by bootleg on 2005-11-06
[http://www.4momo.de/artikel__show_db__netz__95.htm](http://www.4momo.de/artikel__show_db__netz__95.htm) (german, sorry)

[http://www.linuxquestions.org/questions/showthread.php?s=&postid=1172713#post1172713](http://www.linuxquestions.org/questions/showthread.php?s=&postid=1172713#post1172713)

---

### Post by Tadhg on 2005-11-06
i might try installing the driver by ndiswrapper,how do i extract the the exe thoug?

---

### Post by az on 2005-11-06
Often, exe installer are just self-extracting zips.  You can unzip it with unzip


unzip foo.exe

---

### Post by Tadhg on 2005-11-06
right,bit more info. Seems that the card is installed all ok, (although no led's). I reinstalled ubunutu with the card in and now, the card shows up in device manager, iwlist (as ra0) and  ifconfig etc. So the card is there, but i cant seem to ping the router. I have my wep code in perfect afaik (40bit, hex code-same as in the router)

iwlist
>  RT2500 Wireless  ESSID:"Wireless"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s
          RTS thr: off   Fragment thr: off
          Encryption key:XXXX-XXXX-XX   Security mode: open
          Link Quality=0/100  Signal level=-20 dBm  Noise level:-203 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig
> ra0       Link encap:Ethernet  HWaddr 00:11:50:8F:0F:B2
          inet6 addr: fe80::211:50ff:fe8f:fb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11401 errors:0 dropped:0 overruns:0 carrier:0
          collisions:8 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:427692 (417.6 KiB)
          Interrupt:5 Base address:0xc000


any ideas as to wtf i have to do? Any more info i can provide?

---

### Post by Tadhg on 2005-11-06
also get this after "iwlist scan"
> ra0       Scan completed :
          Cell 01 - Address: 00:09:5B:D5:DA:8E
                    Mode:Managed
                    ESSID:"Wireless"
                    Encryption key:on
                    Channel:8
                    Quality:0/100  Signal level:-53 dBm  Noise level:-202 dBm


i presume that means it can see the router?

---

### Post by Tadhg on 2005-11-07
bump

---

### Post by bwainscott on 2005-11-07
I use the same PCMCIA card but used ndiswrapper and the driver that was on the disk.  It is a Broadcom driver that is in a driver folder on the disk that came with the card.  I just sucked it into ndiswrapper and went from there.  WEP setup was a bit painful so I verified I could contact the router and the internet before screwing with WEP keys.  Hope it helps!  Also, mine shows up as wlan0. If you haven't fixed this by tonight, maybe I could email you a copy of the driver I use "bcwl 15" or something like that.  I am at work right now and don't have my linux box with me.

---

### Post by TimAy on 2005-11-07
thanks for the offer but i don't think its a driver problem. The card shows up in device manager and under ifconfig. I haven't a clue after that though. I don't know what the problem is.If i "iwlist scan" my router shows up, but "iwlist ap" doesnt show any peers.Also, "dhclient" doesnt give me any offers. 

Anyone have an idea? Im so bloody frustrated.

EDIT: the plot thickens. Just looking through my router settings on this laptop and it is saying that the linux lappy is attached, i.e. being picked up. So the router,it seems , can see the lappy, but not the other way around. There is obviously something obvious that im missing!i can evan ping the linux from this one.

---

### Post by janne5011 on 2005-11-07
Hi.  check this file:  /etc/resolv.conf
my router is 192.168.0.10
my resolve.conf contains ONLY this:

nameserver 192.168.0.10

I use dhcp
try put in your dns routerip, or that your isp gave you.
after this changed: restart.
hope this helps:).



[QUOTE=TimAy]thanks for the offer but i don't think its a driver problem. The card shows up in device manager and under ifconfig. I haven't a clue after that though. I don't know what the problem is.If i "iwlist scan" my router shows up, but "iwlist ap" doesnt show any peers.Also, "dhclient" doesnt give me any offers. 

Anyone have an idea? Im so bloody frustrated.

EDIT: the plot thickens. Just looking through my router settings on this laptop and it is saying that the linux lappy is attached, i.e. being picked up. So the router,it seems , can see the lappy, but not the other way around. There is obviously something obvious that im missing!i can evan ping the linux from this one.[/QUOTE]

---

### Post by TimAy on 2005-11-07
i checked that file and the ip was 127.0.0.0 so i changed it to 192.16.8.0.1. the dhcp command wouldnt work though. I realllllly dont get this. my iwlist doesnt look quite right either. The MAC address isnt showing up.

---

### Post by janne5011 on 2005-11-07
[QUOTE=TimAy]i checked that file and the ip was 127.0.0.0 so i changed it to 192.16.8.0.1. the dhcp command wouldnt work though. I realllllly dont get this. my iwlist doesnt look quite right either. The MAC address isnt showing up.[/QUOTE]

hey typo only here or?

"192.16.8.0.1"

should be 192.168.0.1

---

### Post by TimAy on 2005-11-07
ah, typo. I put in 192.168.0.1

---

### Post by janne5011 on 2005-11-07
ok. check this in command line first
ndiswrapper -l
should be something like "driver present, hardware present".
to make sure also LOOK in folder so see your drivers really is there
there should be: one inf. file and one .sys file.
(this is from my experience Im new to linux)

then edit the file named "interfaces" I forget where is is do a search.
put in interfacefile:
iwconfig ra0 essid YOURESSID mode Managed key open YOUR-KEYGOES-HERE
dhcpcd RA0

RESTART

---

### Post by TimAy on 2005-11-07
im starting to think of going back to windows. This is ridiculous. The card appears to be installed with all drivers etc but ndiswrapper -l says no drivers installed. Everytime i restart, the WEP code is lost. I haven't a clue what the problem is.

---

### Post by janne5011 on 2005-11-07
hm. you need to redo  the ndiswrapper setup.
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
then edit the interfacefile as said before-
....................

---

