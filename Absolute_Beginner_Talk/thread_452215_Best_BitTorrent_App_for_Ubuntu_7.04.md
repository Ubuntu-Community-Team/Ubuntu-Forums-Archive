---
title: "Best BitTorrent App for Ubuntu 7.04"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Kemical on 2007-05-23
I was wondering what the best bit torrent app would be for Linux Ubuntu 7.04.

---

### Post by delphiguy on 2007-05-23
Personally I use uTorrent via Wine.
Azureus and KTorrent looks good too.

---

### Post by Madpilot on 2007-05-23
I like Deluge, myself. It's a native Gnome program, so  you don't have to use either Wine or KDE libraries, and it's more controllable than the bulit-in gnometorrent.

It's not yet in the Ubuntu repositories, but the Deluge devs have done a .DEB for Feisty that works very well. It's here: [http://download.deluge-torrent.org/ubuntu/feisty/](http://download.deluge-torrent.org/ubuntu/feisty/)

I've been running Deluge for about two weeks now, almost every day, and I've had no crashes/freezes/flakiness, and it's slightly lighter on system resources than running multiple instances of gnometorrent.

Deluge will be in the Ubuntu repos for the next release, apparently.

---

### Post by Kemical on 2007-05-23
I have installed Deluge using Automatix2.
Do ports need to be opened for it to work at fast speeds?

---

### Post by expatCM on 2007-05-23
You may want to consider BitTyrant.  
[http://bittyrant.cs.washington.edu/](http://bittyrant.cs.washington.edu/)
It is based on Azureus and the performance is simply amazing.

Installation is not very friendly though.

---

### Post by PartisanEntity on 2007-05-23
I use Azuerus, have not had any problems with it.

---

### Post by Kemical on 2007-05-23
Did you need to open ports for the downloads to run at a decent speed?

---

### Post by Chemist on 2007-05-23
I use utorrent via wine and don't have any trouble with it. Ever native torrent client I've used I get awful speeds downloading.

---

### Post by Kemical on 2007-05-23
Well yeah, I've noticed that using Azureus. It is downloading something at like 7.5KBP/S. Apparently if you open ports it works better, any idea if that is true?

---

### Post by Hallvor on 2007-05-23
You need to open the right ports in Ubuntu with Firestarter. You also need to open and forward the port(s) in your router, if you have one. It should go much faster.

There is no such thing as the best bittorrent app, IMHO. It all depends what you are looking for; the feature rich and more memory-consuming, or the simple and efficient.

Edit: When it comes to uTorrent, it is being filtered by many users after thy went to bed with bittorrent.com...

[http://www.bluetack.co.uk/forums/index.php?showtopic=16009&pid=77182&st=0&#entry77182](http://www.bluetack.co.uk/forums/index.php?showtopic=16009&pid=77182&st=0&#entry77182)

[http://forums.phoenixlabs.org/t12996-bittorent-and-torrentnow-blocked-in-sourceforge-p2pbts-level-1-list.html](http://forums.phoenixlabs.org/t12996-bittorent-and-torrentnow-blocked-in-sourceforge-p2pbts-level-1-list.html)

---

### Post by Kemical on 2007-05-23
Is there a tutorial on how to open ports to make the connection speed run faster?

---

### Post by pchow98 on 2007-05-24
I am also looking for a BitTorrent client. However, I want to install that onto a CLI only Ubuntu server and control that via HTTPS. I've tried uTorrent and TorrentFlux and didn't really like either because they aren't all that fast and don't really support trackers (using cookie, uid and password, etc.) I've tried Azerus, but it is fat and require GUI interface. I am using uTorrent on my XP machine and it is running quite well, but I want to see if there's something like that on Ubuntu server and without graphical interface.

Thanks in advance.

---

### Post by Donnie Darko on 2007-05-24
Honestly, the best and most stable program I've used is Ktorrent, you can get it with add/remove programs. 
Cheers

---

### Post by orb9220 on 2007-05-24
Yep that is what I use kTorrent in gnome  be sure to get version 2.1.4 deb at ktorrent.org which fixes alot of crashes that were happening on older version.

Deluge I could never get a decent download speed.

---

### Post by Kemical on 2007-05-24
I have installed KTorrent, but I'm still getting a maximum of like 5.5KBp/s downloads. Any ideas?

---

### Post by NeoLithium on 2007-05-24
I've used Azureus, KTorrent, though I find myself running uTorrent in wine, gives me outstanding speed; however I have yet to check out deluge- seems like I might have to.

---

### Post by Kemical on 2007-05-24
Can someone please explain to me how I can make my download speeds run quicker. I have used all your torrent apps and they all seem to do the same thing,

---

### Post by Nythain on 2007-05-24
KTorrent was awesome till the version released with feisty came about... it kept crashing on me when i left my computer unattended.

Switched to uTorrent through wine, get the speed i desire, the options i desire, and better stability.

there has since been an update to ktorrent, but i havent considered reinstalling it to test and see if they fixed my random crash problem yet... if it doesnt crash for you and you are looking for linux native, i would suggest ktorrent

---

### Post by Kemical on 2007-05-24
Well obviously you guys aren't going to answer my question, so I'll just work it out myself then.

---

### Post by orb9220 on 2007-05-24
Impatient? Kemical

> I have installed KTorrent, but I'm still getting a maximum of like 5.5KBp/s downloads. Any ideas?

Did you verify if your ISP is throttling or limiting p2p connections?
Did you try torrents that have alot of seeds/leachers that would have good download speed?
Did you verify that the torrent isn't hosted by Private Tracker which would keep you from downloading unless you are registered?
Did you try [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) to check your upload/download speed?
Did you look into which ports to open if required? Which I didn't have to for my connection But?

Sorry that is all I can think of at the moment.
And try to be a bit more patient it goes alot further in getting help.

---

### Post by Kemical on 2007-05-24
I understand that. But if you go through my posts, I ask the question, and they just reply with another program. Possibly read from the start of the thread before replying with something you know nothing about. :)

---

### Post by orb9220 on 2007-05-24
I am sorry I read thru the posts.

I was not giving suggestions of other programs but the checklist for determining exactly what is wrong with your problem.

Sorry if you are angry with me.

---

### Post by Ek0nomik on 2007-05-24
I use Deluge.  I would get 1MB/s upload at school using it, and now that I am back home I was getting around 500 kB/s download.

Kemical:  Opening ports will get your downloads faster given a few scenarios...

1.  You have a router with a firewall (or a software one) built in and you are connecting to people with a firewall.  Your connections are limited in this case.

2.  If you don't have a firewall and someone else does, the ports are irrelevant (unless the specific tracker has banned the port, but in such a case your speeds will be 0 more than likely).

3.  If you do have a firewall and someone else doesn't, the same applies what I just mentioned.

If there are a bunch of peers (seeders / leechers) your speeds should be fine because chances are other people have their firewall configured properly or don't have one all together.

So, for faster speeds, maybe it's a poorly seeded torrent?  How many peers are there (seeders/leechers)?  Do you have a firewall?  Spill your guys so I can help.  ;)

---

### Post by Kemical on 2007-05-25
Well I tested a download with like 450 Seeders and still going at like 7KBs...I have made a static IP and forwarded a port. However, I have no idea how to connect using that static IP.

---

### Post by Ek0nomik on 2007-05-25
Why a static IP?  What's the difference?

---

### Post by deadlydeathcone on 2007-05-25
Yes, you need to have your ports opened or your DL speeds will mostly be crap. This included ports in both software and hardware firewalls; use the aforementioned Firestarter for the first, making sure ports 6881-6999 for incoming connections are completely open before moving on. Next, you have a few options for routers, as you can use uPnP to automatically forward the needed ports (which requires that your torrent program supports it; Azerous and Ktorrent do; Deluge doesn't)  or manually open the ports through your routers interface. Every router differs in how to do  this, so your best bet is look on[ this site]("http://www.portforward.com/routers.htm") for instructions.

After those steps are finished you have to set your network up to use Static IPs instead of DHCP; it's not that difficult, but requires a chuck of time to accomplish if you've never done it before. It also requires that you know your ISP's DNS servers, although you may be able to get away with using those from the OpenDNS project.

When all of that's finished use a [port scanner]("https://www.grc.com/x/ne.dll?bh0bkyd2") to check out port 6881; if it passes, congratulations. If not, go through orb9220's checklist until it works.

Or you can just live with ~5kb download speeds, which is a pretty popular alternative.

---

### Post by Kemical on 2007-05-25
How can I access Firestarter?

---

### Post by Ek0nomik on 2007-05-25
> **Kemical said:**
> How can I access Firestarter?

```
sudo aptitude install firestarter
```

---

### Post by Hallvor on 2007-05-25
Your problems are probably caused by closed ports (in your router and in Ubuntu) and/or a throttling ISP. Do not use the standard ports for bittorrent (6881-6999), because they are throttled by many ISPs. One open port outside that range will do just fine.

If you have changed the default ports and opened the ports in your router and Firestarter, and you still get bad speeds, it probably means more advanced throttling. Depending on how advanced throttling your IPS is doing, some types can be defeated if you use a bittorrent client with encryption. I know that at least Azureus uses encryption, but I am not sure if it is enabled by default.

---

### Post by walkerk on 2007-05-25
+1 for Deluge. Just make sure your port forward and open the firewall for the app.

---

### Post by cox377 on 2007-05-25
> **Chemist said:**
> I use utorrent via wine and don't have any trouble with it. Ever native torrent client I've used I get awful speeds downloading.

Even Azureus?

---

### Post by darell_m on 2007-05-25
I used utorrent (and really like it comparing all others) under windows but find Ktorrent works just fine when tweaked,  I used the same settings as I learned from utorrent guidelines - especially restrict up load speed ( based on my computer I use 30 Kbs max) and port forwarding (bit tricky as you need to do in router) then tell torrent program what port you want to forward.  My Ubunta FF does not have khelper loaded ( I am a newbie big time with ubuntu) relied on utorrent guidelines which I highly recommend for anyone to help them out.

For anyone wanting to check download speeds do what utorrent suggest and download openoffice,org and it will max your download speed in less than 5 minutes-  for me. Good way to check various settings/tweaks and various torrent programs using same this download. My ktorrent maxed about same speed as utorrent under windows at +200 Kbs, however most normal downloads are much slower except many of axxo's movies.

Als0,  I downloaded utorrent and ran under wine but for some reason could not get the torrent to download with  utorrent even set as default, as the torrent went directly to ordinary dowload page?? However I am so new at all this likely made some really simple mistake,

I will likely give Deluge and others a comparative try, but have many other things to learn in Ubuntu first

All have a good day:popcorn:

---

### Post by mjukis on 2007-05-27
I use Ktorrent but had stability problems in Edgy with it until i upgraded to the latest version from Ktorrents homepage. The performance I have in Ktorrent is superb. I max out my internet connection most times (1700 kB/s). \\:D/

---

### Post by darell_m on 2007-05-27
> **mjukis said:**
> I use Ktorrent but had stability problems in Edgy with it until i upgraded to the latest version from Ktorrents homepage. The performance I have in Ktorrent is superb. I max out my internet connection most times (1700 kB/s). \\:D/

Wish I had your connection!!! at 1700Kbs! but goes to show Ktorrent is OK!;) but each to their own.

---

### Post by wataboutbob on 2007-05-27
I agree. ktorrent is fast and stable for me once tweaked.

---

### Post by nike984 on 2007-06-04
the command that you can use to open your desired port # is

```
sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT
```

This example is for the case opening 6881 port as TCP
You can close the same port by using 

```
sudo iptables -A INPUT -p tcp --dport 6881 -j DROP
```

---

### Post by dustigroove on 2007-06-04
[FONT=Arial][COLOR=Black]Deluge seems to do the trick for me. Clean and simple.

Cheers

[/COLOR][/FONT]

---

### Post by Chang An on 2007-06-23
I like Deluge and Transmission.  I can't believe no one has mentioned Transmission. Transmission is light weight and works great with Xfce.  Both are at getdeb.

[http://www.getdeb.net/app.php?name=Transmission](http://www.getdeb.net/app.php?name=Transmission)

---

### Post by michaelzap on 2007-06-23
I went through almost exactly the same process. I tried Deluge and a bunch of others I was unfamiliar with and didn't much like, went back to Azureus for a while (which I used for a while on Windows), and then when I got sick of the Java bloat I installed uTorrent via CrossOver Office. That worked well (and it was what I had usd most recently in XP), except that I also couldn't get Firefox to download torrents using it automatically (I had to copy and paste the links), and the system tray icon/events didn't work in Ubuntu. So then I checked out kTorrent. It is actually very similar to uTorrent and I haven't had any complaints except for the "Choose which files to download" prompt that bugs me (and the developers say they're going to make optional). If you want a fast and straightforward BT client, I highly recommend it.

---

### Post by Note360 on 2007-06-25
I tested out 3 major competitors on my system on the same torrent, with similar settings.

Azureus was in between with speeds up to 100 kb/s (my internet is slow, usually i can peek at 600 kb/s in windows with utorrent, but i havent been able to get the same speeds)

Ktorrent with 120 kb/s (approx)

utorrent at the bottom with 98 kb/s (approx)

I want to try deluge, but i am getting some weird error. I think i am going to go with Azureus because it has plug-ins and all the features i need as well as speed. However, i am also going to try out deluge (which i loved when i used it then it broke some how).

---

### Post by AriciU on 2007-06-25
Nothing but uTorrent thru wine... and i'm a bittorrent freak.

---

### Post by Ssj3_man on 2007-06-25
Most people i see use _**Azureus.**_

---

### Post by Pzkpfw on 2007-07-07
I just installed ubuntu today  and noticed the drastic drop in torrent downlaod speeds, i used to get max possible for me (about 220kb/s) download speeds using windows with utorrent or bitcomet, on ubuntu the speeds dropped from 7-10 on azeurus to about 90 on bittornado, tested on my usual naruto download which always runs on max, now trying to install deluga (still can't install stuff without first googling for tutorials) and will attempt to mess with firestarter port settings.

---

### Post by deadlikeoscar on 2007-07-07
If you are running Feisty...just go to deluge-torrent.org and click on the i386 package download if that is what you use and download the .deb package. When it is finished click on the file to install it. There are some good plugins by default and it is an amazing client if you ask me. Every release gets even better.;) Sometimes I have heard of issues with saving to an NTFS drive where it starts and stops. If that is the case with you just use the compact storage allocation under the preferences instead. You may have to redownload any problem torrents. I have gotten speeds of up to 900kb/s on private trackers with this client so if it doesn't work for you it is likely a different problem.

---

### Post by Pzkpfw on 2007-07-07
Thanks for the tip, i didn't notice the i386 link, because i went straight to the download section like i was used to on windows.

NTFS is not the case since i ain't got no windows :P, it's just something with ubuntu, since i noticed a lot of posts about slow torrent speed in these here forums.

Now i'll just try to mess around and see what comes out.

---

### Post by michaelzap on 2007-07-07
I don't have any torrent speed issues in Ubuntu, but I did have issues when I switched from Windows to it because of the way that I had set up my LAN and firewall settings. Once I changed those I also had to try some different clients before I found one that I liked that also was fast (some clients - including Deluge - just seemed to download a lot slower, despite doing my best to tweak their settings). I found I got excellent speed using uTorrent (via CrossOver Office), but kTorrent gave me the same download speed and lightweight interface in a native application, so now I use that very happily.

---

### Post by Pzkpfw on 2007-07-07
Ok, everything seems fine to me now, got deluga, opened up the ports, i'm at full power again :D

---

### Post by Gausian on 2007-07-08
so far the best live tried for Ubuntu is Deluge.  Its like the µtorrent of linux.  

not sure why some say its slower, ive been pulling over 1000KB/s with it....no tweaks.

---

### Post by BL00dFox on 2007-07-08
Azureus is all that Ive ever used. It was a laggy piece of.. In WIndows but in LInux its extremely snappy. **Azureus FTW**

---

### Post by kwacka on 2007-07-08
Thanks to everyone who tipped deluge - I installed yesterday and find it vastly superior to azureus, also better than ktorrents.

---

### Post by BL00dFox on 2007-07-08
> **kwacka said:**
> Thanks to everyone who tipped deluge - I installed yesterday and find it vastly superior to azureus, also better than ktorrents.

Hmmm.. This "deluge" seems immensely popular - Ill try it out...

---

### Post by pyros on 2007-07-08
It may be my particular setup, but deluge didn't really work well for me. I prefer a combined approach; Normally I just use the default bittorrent client that comes with Ubuntu. When that fails for whatever reason, I use Azureus, and it comes through for me every time.

---

### Post by kwacka on 2007-07-09
> **Kemical said:**
> Is there a tutorial on how to open ports to make the connection speed run faster?

check out [www.portforward.com/](www.portforward.com/) routers

---

### Post by Efros on 2007-07-09
> **michaelzap said:**
> I went through almost exactly the same process. I tried Deluge and a bunch of others I was unfamiliar with and didn't much like, went back to Azureus for a while (which I used for a while on Windows), and then when I got sick of the Java bloat I installed uTorrent via CrossOver Office. That worked well (and it was what I had usd most recently in XP), except that I also couldn't get Firefox to download torrents using it automatically (I had to copy and paste the links), and the system tray icon/events didn't work in Ubuntu. So then I checked out kTorrent. It is actually very similar to uTorrent and I haven't had any complaints except for the "Choose which files to download" prompt that bugs me (and the developers say they're going to make optional). If you want a fast and straightforward BT client, I highly recommend it.


You can get firefox to save the torrent files to a specific directory, and have uTorrent configured to monitor that directory and automatically start any torrent files it finds there.

---

### Post by djhworld on 2007-07-09
rtorrent

Simple, easy to use and is great with GNU screen.

---

### Post by fedira on 2007-07-09
> **deadlydeathcone said:**
> Yes, you need to have your ports opened or your DL speeds will mostly be crap. This included ports in both software and hardware firewalls; use the aforementioned Firestarter for the first, making sure ports 6881-6999 for incoming connections are completely open before moving on. .

I have a question about the advice that's been repeated about opening ports. Does this make your computer more vulnerable to snoopers etc? Isn't the point of a firewall to keep people out? What effect does it have on security to open these ports? Or is it only particular ports that need to remain closed?

Excuse the perhaps ignorant questions.

---

### Post by Inxsible on 2007-07-09
Does Deluge support selecting which files to download within a torrent ?

I could not find it. I use qBittorrent which gives me that functionality.

---

### Post by dustigroove on 2007-07-09
[FONT=Arial][SIZE=2][COLOR=Black]> **Inxsible said:**
> Does Deluge support selecting which files to download within a torrent ?

I could not find it. I use qBittorrent which gives me that functionality.

It does not appear to be a current or planned feature, however you certainly can file a request for that functionality [here]("http://dev.deluge-torrent.org/query"). Perhaps they'd be open to incorporating that functionality.

Cheers

[/COLOR][/SIZE][/FONT]

---

### Post by halesquad on 2007-07-09
after trying all the other bt clients i have found Deluge to be very simple to use and install and the speed is brill up to 726 on mine, 

[http://dev.deluge-torrent.org/wiki/Downloads](http://dev.deluge-torrent.org/wiki/Downloads)

Ubuntu ¶

As of Feisty, Deluge is in Ubuntu's universe repository. DO NOT INSTALL THIS VERSION

If you want to run Deluge on an earlier version of Ubuntu, you'll have to build the package from source. 

i just installed it from the synaptic and it works brill 

Thank you 

Stephen

---

### Post by deadlikeoscar on 2007-07-09
> **Inxsible said:**
> Does Deluge support selecting which files to download within a torrent ?

I could not find it. I use qBittorrent which gives me that functionality.

Pretty sure it does in the 0.5.2 release.

---

### Post by Eggnog on 2007-07-09
I just installed Deluge from the repository and downloaded a couple of quick torrents with it.  I didn't see an option to choose which files in the torrent I wanted to download like I did with uTorrent in XP and Ktorrent under Gnome.  The option may be there but I may not have seen it or turned it on or something.  If that option isn't there yet, however, I may wait until it is before I use it.  It's a pretty nice app, though.

---

### Post by deadlikeoscar on 2007-07-09
Uninstall the one in the repos and go to deluge-torrent and download the .deb for 0.5.2. or use the svn. They don't have the option to do it before you start downloading but once it is started, click the files tab for the individual torrent you want to download part of and uncheck the ones you don't want or use the uncheck all option if you only want a couple files. It should work in this release. Plus, they have some awesome plug-ins you can add.

Edit- it does work, just tried it but couldn't get the unselect all option to work. There is also an individual file progress bar on the right.

Edit2- If you right click on a file in the files tab and select "select all" and then uncheck a box it will unselect all of them.

---

### Post by vishzilla on 2007-07-10
You can....go to the files tab below and select the files you want to download

---

### Post by Golyadkin on 2007-07-10
I have been running Deluge 0.5.2 for a while now as well, and what I like is that it supports uTorrent PXE, DHT and all other extra features :)

---

### Post by Inxsible on 2007-07-10
> **deadlikeoscar said:**
> Pretty sure it does in the 0.5.2 release.
 
yeah I was using the 0.5.1 as that is the latest stable version. I did like Deluge...it was pretty simple to use..
 
But so is qBittorrent :)

---

