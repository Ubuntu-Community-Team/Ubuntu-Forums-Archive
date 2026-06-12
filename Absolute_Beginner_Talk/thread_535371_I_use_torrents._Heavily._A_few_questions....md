---
title: "I use torrents. Heavily. A few questions..."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2007-08-26
What client should I use to download torrents in Ubuntu?

---

### Post by chrome307 on 2007-08-26
What did you use before?

If Windows based you could try them in WINE eg uTorrent.

You can also use Azureus or KTorrent available from the Applications ---> Add & Remove

---

### Post by jfinkels on 2007-08-26
rtorrent

No need for a GUI when you're just downloading files...

---

### Post by Steveway on 2007-08-26
Deluge on Gnome or XFCE, Ktorrent on KDE and rtorrent for the Commandline.

---

### Post by papuccino1 on 2007-08-26
Well, I use uTorrent right now.
(I'm writing this from Windows)

I really want to get into Ubuntu and learn. I'm very curious.

Could I possibly trouble you for screenshot of rTorrent? I don't really need a GUI but *some* would be nice.

---

### Post by kostkon on 2007-08-26
[KTorrent]("http://ktorrent.org/") is a very good client! You can find it in *Synaptic*. Don't forget to enable the *Backports* repository in your *Software Sources* in order to get the latest version.

---

### Post by Acglaphotis on 2007-08-26
ktorrent

---

### Post by papuccino1 on 2007-08-26
Thanks for the QUICK answers. Ubuntu community truly is remarkable. Thanks again guys...

---

### Post by randomjohn on 2007-08-26
torrentflux and tf-b4rt are very good for remote web administration of your torrents

---

### Post by bogolisk on 2007-08-26
My favorite is Transmisson (0.80 or later)

[http://www.getdeb.net/app.php?name=Transmission](http://www.getdeb.net/app.php?name=Transmission)

It's gui client but if you ssh to your machine to can query/control the running Transmission session using the command line. It's great for controlling your torrent session away from home.

---

### Post by lmlypfan on 2007-08-26
Simple question.

Why when torrent clients are brought up, many people suggest wine with utorrent?
Why not just you ktorrent natively in ubuntu, or any other BT client?  I have used utorrent in the past and understand that it is a good client, but if a perfectly good solution is available without windows, why run wine for utorrent?  I thought I read lately that utorrent is going closed sorce, so another reason to avoid it.

Thanks

---

### Post by mikewhatever on 2007-08-26
> **papuccino1 said:**
> What client should I use to download torrents in Ubuntu?

Slightly off topic, but, that was only one question.

---

### Post by insane_alien on 2007-08-26
Ktorrent if you want a GUI

or my personal favourite: rtorrent no GUI but it does everything. i run it on my 'bit box' its basically a always online bittorrent client/server and a NAS.

---

### Post by chrome307 on 2007-08-26
**@ Imlypfan**

It's a recommend torrent client to be used on some sites - therefore if he was using this before he could continue to use this for the time being until he felt comfortable using another client.

Also I took onboard that he's a heavy torrent user, therefore being offline might not be productive in this instance for him whilst he undertakes his learning curve.

---

### Post by Bout to Snap on 2007-08-26
> **papuccino1 said:**
> Thanks for the QUICK answers. Ubuntu community truly is remarkable. Thanks again guys...

i went completly cold turkey after my windows systems kept getting infected and crashing hated to lose the gaming options but it's well worth if after you get your stuff set up with linux, Just like you i torrent a lot to and on windows i also used Utorrent after coming to the linux community i went with Ktorrent has a nice Gui with a Nice proformance i would highly suggest using this tool for torrents. And personally you couldnt find support like this forum offers for the windows operating system,however i would suggest you do the dual boot method untile you feel comfortable enough with Ubuntu.

---

### Post by obscur156 on 2007-08-26
I will say Ktorrent and you can use the IP filter in it if your paranoid just like me ;)

---

### Post by spacegypsy on 2007-08-26
Azureus
 &
Deluge

---

### Post by ign on 2007-08-29
I'm tented to install rtorrent on my home file server. is there a way to control rtorrent remotely, maybe from a web browser or using a widget like [this one]("http://andrewdupont.net/azureus/")?

---

### Post by Mornedhel on 2007-08-29
Just login to your home server with ssh. (Provided you have an SSH server on your home server.)

---

### Post by ign on 2007-08-30
do have an ssh server, but i think it's a pain having to do all that typing each time i want to download a torrent....
i wanted to install and check, but after reading the forums a lot of people seems to have problems with the installation, what has been your experience?

---

### Post by BlackMeTaL on 2007-08-30
> **lmlypfan said:**
> Simple question.
Why when torrent clients are brought up, many people suggest wine with utorrent?
Why not just you ktorrent natively in ubuntu, or any other BT client? 
Thanks

Personally I still run uTorrent in Wine. Why? I've tried just about every other client and every other client had something that bugged me. (Azureus, Deluge, KTorrent, rTorrent)
Why would I use anything else when uTorrent with Wine works _exactly_ as I want it to.

---

### Post by hyper_ch on 2007-08-30
oh well, I used ktorrent for a long time and liked it but now I switched to rtorrent... having access by SSH is just great...

There are two web-guis being developped... one is already there for testing but it requires a newer version that the on in the repos...

---

### Post by rahimveron on 2007-08-30
My goat goes to Deluge

---

### Post by Mornedhel on 2007-08-30
> **ign said:**
> do have an ssh server, but i think it's a pain having to do all that typing each time i want to download a torrent....
i wanted to install and check, but after reading the forums a lot of people seems to have problems with the installation, what has been your experience?

No problems whatsoever. I wasn't even aware people had been having problems (but I use it on my own laptop, so obviously, I don't have to deal with SSH'ing anywhere - however, I know one person who installed it on his Debian server and uses it via SSH, and apparently the installation process went as smoothly as possible, but this guy has way more experience on Debian than I have). I just apt-got it and forwarded ports on my router, which you have to do anyway for every client out there (I hear ktorrent has something special on that issue, though).

Otherwise, as hyper_ch said, there's at least one web GUI in the repositories.

1st edit : rahimveron, Deluge is not available through the reps, is it ? (apt-cache search deluge does not return anything) I'll test it anyway, since you're not the first one to recommend it.
2nd edit : OK, so the Feisty package is on the Deluge website.

---

### Post by hyper_ch on 2007-08-30
Well, installing a ssh server is not difficult:

```

sudo apt-get install openssh

```

And then you just need to forward port 22 (or whatever port you made the server listen to) from the router to you actual computer if you are not directly connected to the net...

Then run rtorrent in "screen" and it's marvelous...

---

### Post by jusmurph on 2007-08-30
I'm a deluge fan.

It's not brilliant, but its not resorting to wine either!

---

### Post by NorthernPaladin on 2007-08-30
I recommend azureus 2.5, In my comp it works fastest of the available clients( or of those that I have tested)

---

### Post by swoskow on 2007-08-30
> **hyper_ch said:**
> oh well, I used ktorrent for a long time and liked it but now I switched to rtorrent... having access by SSH is just great...

There are two web-guis being developped... one is already there for testing but it requires a newer version that the on in the repos...


Which bittorrent client you use really comes down to personal preference and what you want to do.  The suggestions people posted are all good and unless you specifically want utorrent, thier is no need for going through Wine.  I torrent a lot and have used many different clients.  I have settled on Azureus (I know all the arguments against Azureus) because it does what I want to do (see below). As per a web based client, thier are a number of excellent options in Ubuntu.  SSH has already been discussed and is very simple to set up in Ubuntu.  I have torrentflux (use torrentfluxb4rt) set up on my Ubuntu box (search the forum for a How To).  It is really just a web based front end gui that can use any number of clients on the backend (the default is bittornado).  It can be difficult to set up but it works great.  Personally, I settled on Azureus (2.5) because of Azsmrc.  Azsmrc is a web based server/client plug-in for Azureus.  I like it because I have a Linux, Windows and Mac box on my home server and Azsmrc is platform independent (no need for Putty).  I use my Linux box as the server and I have Azsmrc on all the other computers.  It was very simple to set up and it allows me to torrent from any computer on my network.  I have file sharing via Samba and SSH set up so I can also access the downloaded files from any computer on my network.  Azureus also has an html web interface and swing ui as other web based options.  You have lots of excellent bittorrent options in Ubuntu, its just a matter of finding one that fits your needs.

---

### Post by notwen on 2007-08-30
Gnome user running kTorrent here, it's a nice simple user interface and has enough customization to suit my needs. =]

---

### Post by ltk5 on 2007-08-30
What about BitTornado? :)

---

### Post by bogolisk on 2007-08-30
> **notwen said:**
> Gnome user running kTorrent here, it's a nice simple user interface and has enough customization to suit my needs. =]

You should try Transmission-0.80, a gtk program so it uses gnome theme. Dead simple program and the devs followed the same moto as ubuntu: "it just works". It support remote control so at home I use its gui and from work I can control it via ssh. It runs 24/7 on my box!:) IMO, the only feature(s) lacking from Transmission is the ability to snub/kick/ban peers. I don't care about those things because I don't babysit torrents, I tend to start a torrent and check it the next day.

Get the feisty package from getdeb.net

Deluge is currently too buggy for my taste. The last time I tried it, my partial download (when you only download some files from a torrent) was all corrupted. The same partial download was correct with Transmission and rtorrent. BitTornado is probably the most reliable client but it's interface is not very convenient.

---

### Post by s26c.sayan on 2007-08-30
+1 to [Transmission]("http://transmission.m0k.org/") !! :)

The latest release has a number of new features, like creating torrents. Plus it is simple & lightweight, yet feature filled, and just works!!!

---

### Post by ign on 2007-08-31
First of all, thanks for your replies :)

Ok, I installed rtorrent and now I can see why people love it, it runs seamlessly on a slow machine and use very little resources. I also love the interface.

I had some problems with the config file (missed a how to), but figured out almost everything through this forum and a bit of google.

I still have a couple of problems, I'm not sure about the configuration I have. It actually works, but I think it should be faster, based in the previous results with azureus and transmission. "Watch a directory for new torrents", which is one of the most important features, is not working either.

Do you lnow where I can find a very step by step config tutorial (I'm talking about editing the .rtorrent.rc file) or maybe a working example of this file?

---

### Post by Magneticgravity on 2007-08-31
Is Azureus any good on Linux? On Windows it was pretty fast.

---

### Post by zachtib on 2007-08-31
> **bogolisk said:**
> Deluge is currently too buggy for my taste. The last time I tried it, my partial download (when you only download some files from a torrent) was all corrupted. The same partial download was correct with Transmission and rtorrent. BitTornado is probably the most reliable client but it's interface is not very convenient.

We've since fixed that issue.  A lot of progress has been made in the past few months, and Deluge has become much more stable.

---

### Post by shrynakesavan on 2007-08-31
i have tried almost all of the majour torrent clients except for torrentflux coz i heard its main potential is as an server based client... well everything sucked for me.... from azurus to bottornado  , gnome, ktorrent, deluge... rtorrent .. all sucked (for me()... no offence meant guys... but i had a loads of problems installing wine and starting utorrent.... but i had nochoice coz all the others failed me... thy were all slow ... none of them gave me the speed which i used to get in amy windoys xp... so i finally installed utorrent... and its the only client with gives me the same speed  as my EX-XP,, so since then .. its been no turning ack for me... i look forward to the day when we could use an indegenous gnome based client of equal efficiency.... without wine or anythingl,... but ironically till then wine+utorrent rulezzzzzzzzzzzzz!!!

---

### Post by hyper_ch on 2007-08-31
That's the homepage of rtorrent:  [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

Here's the user guide:  [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

And here are some common tasks:  [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

Official support channel is at:
irc.worldforge.org
#libtorrent

Btw, you do run rtorrent within screen, right?

The watch directory works perfectly for me... I donwload a new torrent in there and it starts doing it things :)

---

### Post by cozmicharlie on 2007-12-22
> **Magneticgravity said:**
> Is Azureus any good on Linux? On Windows it was pretty fast.

I have used Azureus on Linux and never had any problems with it.  The key is to be sure you have the correct Java installed.  Also, for those interested in networking there are great plug ins for Azurues.  I have written a tutorial on using Azureus over a network with the AzSMRC server/client plugin that you may find helpful ([http://ubuntuforums.org/showthread.php?t=637160&highlight=azsmrc](http://ubuntuforums.org/showthread.php?t=637160&highlight=azsmrc))

---

