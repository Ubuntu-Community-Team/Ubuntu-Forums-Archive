---
title: "struggling with torrents"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-07-18
i've pretty much got everything set up on my first full ubuntu install - video codecs, XMMS player and everything else.

i'm just having real difficulty getting any kind of torrent program off the ground.

as an example, i'm trying azureus at the moment and I always have "DHT Firewalled" - all the time.

i've read various threads and things about opening ports, but i wouldn't have the faintest idea on how to do that.

i'm using a sagem fast 800 modem on the TalkTalk ISP (if you're in the UK).

would anyone know of an (big) idiot guide that I could look at the help get me off the ground and torrenting ??

cheers.

---

### Post by aktiwers on 2007-07-18
After a quick Google search on your ISP it looks like they are traffic shaping your connection! I hate when ISP's do that. :(

Well, in Azureus you can try to Encrypted traffic. 

Open op Azureus and go to:
Tools => Options

Then go to:
Interface => Mode

And set it to   "Advanced".

Now, still in the options menu, go to:
Connection => Transport Encryption

And set it like mine on the screenshot below.

Let me know if it works :)

---

### Post by Frak on 2007-07-18
Are you going through an additional router such as a WiFi Access point?

---

### Post by jasonwatkins on 2007-07-19
no, it's just a normal USB ADSL Modem connected directly to my machine.

i've also set the encryption as well, so i'll see what happens - thanks ! :)

---

### Post by splintercellguy on 2007-07-19
For the port forward dealio try portforward.com and see what port Azureus is using.

---

### Post by jasonwatkins on 2007-07-19
that portforward site didn't really help me i'm afraid - thanks though.

i'm running azureus at the moment, with the encryption set.

if i run the "NAT/Firewall Test" option, it tells me the incoming TCP listen port is 36627 and if i click "Test" it says it's ok.

i've got one test torrent set up, which has 5 seeds, and the tracker status is "OK" as well.

at the bottom of the screen, the "Ratio" button is green, the "NAT OK" button is green, but it's STILL "DHT Firewalled".

---

### Post by splintercellguy on 2007-07-19
You don't have to worry about DHT, I sometimes get that too :).

---

### Post by jasonwatkins on 2007-07-19
> **splintercellguy said:**
> You don't have to worry about DHT, I sometimes get that too :).

it never changes though - my torrents have plenty of seeders and loads of leechers, but i get ZERO download speed ..

---

### Post by splintercellguy on 2007-07-19
Tick off the encryption, because a lot of people don't support it. And get a better torrent if you can :).

---

### Post by jasonwatkins on 2007-07-19
ok, i'll test it out with a torrent with huge seeds - i know on mininova, some of the anime torrents get over 2500 seeders, so i'll see what happens ..

*edit - i've just downloaded a torrent with 23,000 seeds so we'll see :)

---

### Post by weth on 2007-07-19
maybe this could help you:

" the whole performance of DHT Network will become better if you enable the port forwarding of the UDP port in your firewall/NAT."

why don't you try Ktorrent instead of Azureus?

:)

---

### Post by corevette on 2007-07-19
You're fine leaving encryption on
The problem is your router has a firewall and you need to open up the port that Azureus uses so it can access  other peers to download from
Unfortunately, I'm not good with port-forwarding
Try going to your router manufacturer's website

---

### Post by jasonwatkins on 2007-07-19
i tried ktorrent and had the same problem - zero download speeds.  i've looked at the website for the router and DNS settings, but it's pretty much like reading klingon .. i'm just a lowly programmer, not a network guru :D

i need to go out now, so i can't come back to this until later unfortunately, but thanks for all your help and suggestions so far ..

---

### Post by Frak on 2007-07-19
Seriously, try &#956;Torrent or Deluge, they are very popular torrents, and you may get better results with those.

---

### Post by jasonwatkins on 2007-07-19
i've just gone back and tried ktorrent and remembered why i tried azureus in the first place - my torrents in ktorrent were/are permanently stalled.

in an ideal world, i'd like to use a linux native torrent program because that's the whole point of me ditching XP, but if the worst comes to the worst, i'll have to wine something i s'pose ..

---

### Post by aktiwers on 2007-07-19
Else try go to your :
192.168.1.1 

in firefox and look if you can turn of that Firewall. I think thats the IP of your Modem.
Or atleast if its not, find the IP of your Modem and look if you can go in there and turn of the firewall or open the port for Azureus.

---

### Post by Frak on 2007-07-19
Or try 192.168.0.1

---

### Post by jasonwatkins on 2007-07-19
ok, i've tried entering both those IP address directly into firefox as

[http://192.168.0.1](http://192.168.0.1)

and 

[http://192.168.1.1](http://192.168.1.1)

and after waiting for a fair while, it just comes back with an error saying can't establish connection - i've tried unplugging and plugging back in to drop the net connection, but still get the same problem - only the error message comes back a lot quicker !

i've googled for 'talktalk modem ip' and 'sagem fast modem ip' and tried a few random ip's and can't connect to the modem in any fashion.

i'm losing patience with this frakkin' thing now ..

---

### Post by kelvin spratt on 2007-07-19
[http://portforward.com/routers.htm](http://portforward.com/routers.htm) This will give you step by step instructions on how to set up port forwarding and your app when i used it  torrent was not listed i used instructions for azures and changed the  Azur1
To Ktor1 and used port 61401 and i max out with ktorrent so nothing wrong their

---

### Post by jasonwatkins on 2007-07-19
> **kelvin spratt said:**
> [http://portforward.com/routers.htm](http://portforward.com/routers.htm) This will give you step by step instructions on how to set up port forwarding and your app when i used it  torrent was not listed i used instructions for azures and changed the  Azur1
To Ktor1 and used port 61401 and i max out with ktorrent so nothing wrong their

thanks for that, but i tried that website earlier today and it doesn't help because my usb modem is a sagem fast 800 and this site doesn't have instructions for that model.

---

### Post by jasonwatkins on 2007-07-19
just for interests sake, i re-installed deluge and added the torrent that has 23,000 seeds.

at the moment, it's picked up 60 seeds (and climbing steadily) and 78 peers and has a download speed of 0.1kb/s.

if i had 60 seeds in utorrent in windows, that file would be downloaded inside 2 minutes flat.

---

### Post by BlahMan_of.Doom on 2007-07-19
Eh heh...heh..here's the thing about um...Deluge..

Data gets sent to a server about what you're downloading..it's a nice client and all but you know...if you happen to be downloading anything illegal then..well..um..have a nice day.

I recommend [KTorrent](http://ktorrent.org/). No, you don't need KDE. It has a nice interface. Make sure you change the time algorithm to current speed, rather than the average speed.

EDIT: I see the issues you are having with KTorrent. For example, you could forward port 15150 on your router and firewall, and make KTorrent use 15150.

---

### Post by jasonwatkins on 2007-07-19
> **BlahMan_of.Doom said:**
>  For example, you could forward port 15150 on your router and firewall, and make KTorrent use 15150.

I don't know how to do that ... that's why i tried the IP addresses and the portforwarding website for some idiot guide on how to connect to my modem but i've had no luck.

even googling for "torrents sagem fast 800" and "port forwarding sagem fast 800" doesn't give me any clues, unless i'm being incredibly stupid (which is highly likely :D).

sorry to be such a pain

---

### Post by jasonwatkins on 2007-07-20
ok, so there I was - 12:30am and in some random chatroom because I was bored and frustrated with this stupid torrent problem.

I decided to call it a night, and as I was shutting everything down I thought to myself "hhmm, what if i fire up ktorrent and give it a try ?.  I know they used to throttle the p2p and torrent stuff during the day, but it's half past midnight so it's got to be worth a punt".

so i fire up ktorrent and add my torrent with 23,000 seeds.  I sit and watch as it picks up seed after seed and rises to 60 seeds and 98 peers.

i sit and watch the download speed get up to 62.2kb/s as well ..

*sound of a stylus being pulled off a vinyl record*

:)

yes, it appears to be working !

giving it some thought, I have to wonder if it's as simple as my ISP throttling the downloads more severely than i'd realised.

i know i used to get the odd speed of 2-3 kb/s during the day on XP,  but it was still something.

I'm just wondering if it's a side effect of Linux, or the way I connect to the internet, that the throttling is more severe and doesn't register any speed.

Even the DHT connection worked :)

Anyway, as far as I'm now concerned, i'm happy.  I'm used to doing all my downloading overnight as it is, so if this particular torrent i'm downloading takes another few days then it's not a problem in the grand scheme of things.

so if any mods are reading this, then please feel free to add a "[SOLVED]" to the forum title, and thanks for everyone's help and patience :D

---

### Post by Frak on 2007-07-20
It was probably because most clients seed at night when the computer is not in active use. Just like how Fold at Home works. Use CPU that would otherwise be wasted, but in this case, seed and not waste bandwidth.

---

### Post by dkaddict on 2007-07-24
I really don't pay too much attention to forwarding ports and what have you. I get really good speeds with Ktorrent and utorrent run through WINE without enabling upnp or forwarding anything. I use a high number for the port KTorrent listens on (92440 or something like that) and just let utorrent pick a random one each time I use it. My uploads on both are set to unlimited and I seed files all the time I have it running. When it is going good, I get an average of 500kbps.

Now for the catch. After a little while trying to figure all of this torrent stuff out, I discovered 'bandwidth throttling'. It has been described earlier in this thread as 'Bandwidth Shaping' and that is what may be your problem. My ISP, British Telecom, throttles Bit Torrent downloads between 4pm and Midnight every day. They do so, apparently, in order reduce the load on their servers at 'peak times'. My Torrents, which fly in at nearly half a mega byte a second, drop to 12kbps MAX. I am trying to figure out how to get around this behaviour that my ISP uses to restrict what was sold to me as 'unlimited 8MiB broadband'. It ain't 8meg and it ain't unlimited. End of.

I suggest doing a Google search for 'Bandwidth Throttling' in whatever country your ISP is based. British Telecom aren't the only ISP in the UK who do this.

If you want to see how well Bit Torrents work, do the following>

Download a torrent file of your liking. Make sure it has plenty of 'seeders'.

Open file with Ktorrent or utorrent in WINE. Do so at, say 6am (YEP, Get up early or have an all nighter-2am to 6am are the best times for me).
In Ktorrent, open up settings or preferences and change the port to listen on to a higher number-this shouldn't matter though as it never has for me, I just do it to be double sure.

Don't enable upnp, it has only made mine slow. Play about with the rest to get best speed. Utorrent can be left as it is and I get a 700mb file in about 20mins (40max) Which, all things considered is plenty fast enough I reckon.

I have been down the port forwarding road and found it to be a windy, cumbersome path which rarely bore any fruit. It just complicates matters IMHO. But then again, I am just a reformed Joe Bloggs point click merchant who spent twenty years prior to finding Ubuntu imprisoned in Novell land.

My early experience of Ubuntu taught me one thing pretty quick>>to buy a half decent ethernet router. I got a Netgear DG630, (I think. on't use it no more got a new one) ditched the USB heap of rubbish, and my net speeds more than *_doubled_*. ADSL USB modems are really no good. £30 will change your experience for the better.

Hope I have helped.

(Hijack time) If anyone knows how to beat the bandwidth shaping I have described, please please please tell. I want UNLIMITED COS THAT'S WHAT I PAY FOR

---

### Post by kjp1956 on 2007-12-26
I was just looking thru threads because I also had a download problem. Did just what you said to do and everything worked just fine.
Thanks
kjp71956

---

