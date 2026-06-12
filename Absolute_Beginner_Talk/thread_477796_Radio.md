---
title: "Radio?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-18
Hi, how do i listen to radio in Ubuntu 7.04, by that i mean Windows media player based radio and real player based radio?

Here is the websites of the radio stations i want to listen to, some of them are in a strange foreign language called Norwegian. Just ignore them if you don't understand Scandinavian 
[http://www.bbc.co.uk/radio/d/]("http://www.bbc.co.uk/radio/d/") (English) 
[www.radio1.no]("www.radio1.no") (Norwegian)
[http://www24.nrk.no/p3/]("http://www24.nrk.no/p3/") (Norwegian)

---

### Post by annda on 2007-06-18
have you got all the codecs and plugins installed?

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Players_.26_Browser_Plug-ins)

using those, i can now hear nice music on nrk 3 :-)

p.s. for best results, restart FF or even your system

---

### Post by ajmannen on 2007-06-18
Might be working for you, but not for me:(

---

### Post by nutz on 2007-06-18
See if you have these installed...

---

### Post by ajmannen on 2007-06-18
yes i have that
[[img]http://bildr.no/thumb/77943.jpeg[/img]](http://bildr.no/view/77943) here is what happens when trying to start anny of the radio stations

---

### Post by ajmannen on 2007-06-19
Anny one?, I have only ubuntu on the computer and i'm starting to miss the radio :(

---

### Post by st0nes on 2007-06-19
Hi,

I downloaded and installed the Linux version of realplayer and it worked right away.  I listen to BBC radio Devon and Capetalk; I haven't tried it with any other streaming stations.  It also plays podcasts &c.  I'm at work at the moment and the Websense nanny won't let me into the realplayer site to give you the links.  Anyway, try it and see if it works for you.

---

### Post by REDISISTone.nl on 2007-06-19
Hi!

I dont think your the only one with this problem...I think my system is having the same problem...I can't play radio (I can't even play movies in TotemXine?) I deleted all packages and reinstalled them again...Nothing...

VLC does the job for playing movies but streaming media in FF doesn&#8217;t work (except for flash streams)

I'm using Feisty...

---

### Post by Golyadkin on 2007-06-19
I installed the realplayer plugin for Firefox and I can listen to the BBC Radio ([huge list of stations here]("http://www.bbc.co.uk/radio/aod/index.shtml")).  I am running 32 bits Firefox in 64 bits Ubuntu (because of the Flash problem)

---

### Post by arochester on 2007-06-19
I can hear [www.Radio1.no](www.Radio1.no). Install an add-on in Firefox called "Download Embedded" It will put a red arrow in your browswer on the right bottom corner. Open the [www.Radio1.no](www.Radio1.no) page. Click on "Lytt til Radio 1 live". That will open another window which says Additional Plugins are required - ignore that. Click the red arrow>View embedded items. Download the R1B96.asx. Open it (my machine want to open it in Democracy Player but close that.) It will save a file R1B96.asx. I opened it with VLCPlayer. It showed a short advert (Tropicana and something by Quaker- Rug Fras) - then it started streaming.

Just clicked on R1B96.asx. Opened with Kaffeine. No advert. Instant streaming

---

### Post by arochester on 2007-06-19
Just heard [http://www24.nrk.no/p3/](http://www24.nrk.no/p3/) too. Same as before. File =
[http://nettradio.nrk.no/php/includes/channelstreamingurl.php?pichannel=p3&quality=m](http://nettradio.nrk.no/php/includes/channelstreamingurl.php?pichannel=p3&quality=m). Open with Kaffeine. A bit of a pause, then it came on.

---

### Post by e6626550w on 2007-06-19
> **ajmannen said:**
> Hi, how do i listen to radio in Ubuntu 7.04, by that i mean Windows media player based radio and real player based radio?

Here is the websites of the radio stations i want to listen to, some of them are in a strange foreign language called Norwegian. Just ignore them if you don't understand Scandinavian 
[http://www.bbc.co.uk/radio/d/](http://www.bbc.co.uk/radio/d/) (English) 
[www.radio1.no]("http://www.radio1.no") (Norwegian)
[http://www24.nrk.no/p3/](http://www24.nrk.no/p3/) (Norwegian)

Below is a good tutorial on not only listening to internet radio via VLC but also how to record it at the same time. VLC will do about anything I've found. For instance, with the Firefox plugin MediaPlayerConnectivity installed I can watch MLB.TV in Linux with VLC and MLB doesn't support Linux, they are a whore for Bill and Melissa. Once somebody told me how to do this, I was able to eliminate windows off my computer because watching those silly games was the only reason I was keeping XP around. 

[http://tinyurl.com/6suup](http://tinyurl.com/6suup)

eileen...

---

### Post by e6626550w on 2007-06-19
To follow up on my last post, I just clicked the BBC site and it looks like they are using a RealAudio stream. This makes listening to them really easy if you have MediaPlayerConnectivity installed in FireFox. I don't believe VLC will play a RealAudio stream. 

[http://tinyurl.com/2m8w2z](http://tinyurl.com/2m8w2z)

When you click on the icon at BBC for the stream you want, a black screen will appear that has an icon that looks like a  reel of film in it. Click on the film and Realplayer should open right up and play for you. 

eileen...

---

### Post by ajmannen on 2007-06-19
How did you make it work with Kaffin, i can't get it to work at all..

---

### Post by arochester on 2007-06-19
Have you got the various multimedia codecs installed? I have found that the easiest way to install them is though Automatix2 at [http://www.getautomatix.com/](http://www.getautomatix.com/) (- Although some people don't like Automatix...)

---

### Post by moore.bryan on 2007-06-19
[SIZE=3][FONT=Century Gothic][I][SIZE=2]if the stream/content uses windows media player (wmp) to play it, you'll need some tinkering.  i use iceweasel (firefox), so i just installed the [mediaplayerconnectivity plugin]("https://addons.mozilla.org/en-US/firefox/addon/446").  for other streams, you may want to install streamtuner (it's in the repos, maybe medibuntu repo)... it has tons of choices and uses xmms, which--i would guess--would allow it to be used with audacious as well.
[/SIZE] 
[/I][/FONT][/SIZE]

---

### Post by ajmannen on 2007-07-02
Nothing wokrs, ok. Radio 1 works now but P3 still won't work
[[IMG]http://img267.imageshack.us/img267/6892/screenshotjj3.th.png[/IMG]](http://img267.imageshack.us/my.php?image=screenshotjj3.png)

---

### Post by sundial on 2007-07-20
Can someone tell me how to install Real Player in Ubuntu 7.04?  I can down load the file but it is not self installing.  What can I do?  I tried other apps to listen to Internet Radio but none seem to work for me.

---

### Post by nutz on 2007-07-20
Check out an app called Songbird. It is a Mozilla product and so far I kind of like it...

---

### Post by candtalan on 2007-07-20
> **ajmannen said:**
> Hi, how do i listen to radio in Ubuntu 7.04, by that i mean Windows media player based radio and real player based radio?

Here is the websites of the radio stations i want to listen to, some of them are in a strange foreign language called Norwegian. Just ignore them if you don't understand Scandinavian 
[http://www.bbc.co.uk/radio/d/]("http://www.bbc.co.uk/radio/d/") (English) 
[www.radio1.no]("www.radio1.no") (Norwegian)
[http://www24.nrk.no/p3/]("http://www24.nrk.no/p3/") (Norwegian)

this is from a uk list in answer to a similar question from me, and it worked ok:

> Add the medibuntu repo as per these instructions - this is so you can
> install the necessary codecs.
> [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)
> 
> sudo apt-get update
> sudo apt-get remove totem-mozilla
> sudo apt-get install mozilla-mplayer w32codecs
> 
> You should then find that opening firefox and going to any of the bbc
> realplayer pages you can click "play in realplayer" and it should work
> in the browser.


note: I did have radio working ok previously with realplayer (proprietary binary) but I got some complications I think on video on bbc sites, so I totally removed all realplayer related files (long job....) manually and followed the above actions.
good luck

---

### Post by sundial on 2007-07-20
Thanks for the responses.  I saw the earlier threads.  I want to listen to USA Talk radio stations that I cannot get off the airwaves.  I am able to do so using Real Player on my Windows system.  I want to be able to do so using Ubuntu.  At least one suggested a way to do this for BBC radio. That is not my interest at the moment.  Any further suggestions?

---

### Post by nutz on 2007-07-20
> **sundial said:**
> Thanks for the responses.  I saw the earlier threads.  I want to listen to USA Talk radio stations that I cannot get off the airwaves.  I am able to do so using Real Player on my Windows system.  I want to be able to do so using Ubuntu.  At least one suggested a way to do this for BBC radio. That is not my interest at the moment.  Any further suggestions?


Have you tried running the Winows version of real player via Wine? I have never tried running that app in Wine but I wouldn't be suprised if it works.

---

### Post by sundial on 2007-07-20
No I have not tried to use WINE. I would rather get a app that is designed to runs in Linux.  I am trying to keep this system stable and lean.  The more crap I pile on it the slower it gets and soon it will be just like Windows.  That is not why I am trying to switch over to Linux.  Thanks for the thought.  At some point I might just try it, but not right now.

---

### Post by nutz on 2007-07-20
The reason I sugested that is because the channels you are looking for may be exclusive to real player. And unless there is a Linux port of the real player you pretty much have no choice but to use the Windows one if you really want to hear those channels. Many online radio services are doing this to force people to use a player of their choosing.

---

### Post by sundial on 2007-07-20
There is a port of the Real Player to Linux.  I can download it but have no idea how to install it.

---

### Post by nutz on 2007-07-20
> **sundial said:**
> There is a port of the Real Player to Linux.  I can download it but have no idea how to install it.


Have you seen this?

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

[http://www.linuxforums.org/forum/ubuntu-help/63528-installing-bin-ubuntu.html](http://www.linuxforums.org/forum/ubuntu-help/63528-installing-bin-ubuntu.html)


Google is the magic answer source. It installed perfectly for me with the instructions on that page. See if that gets it working for you too...

---

### Post by candtalan on 2007-07-23
> **sundial said:**
> Thanks for the responses.  I saw the earlier threads.  I want to listen to USA Talk radio stations that I cannot get off the airwaves.  I am able to do so using Real Player on my Windows system.  I want to be able to do so using Ubuntu.  At least one suggested a way to do this for BBC radio. That is not my interest at the moment.  Any further suggestions?

How sure are you that the suggestion for bbc radio will not work for your own needs? 
BBC requires realplayer  streams to be used. It is probably a typical example of any station using realplayer streams.

---

### Post by sailor2001 on 2007-07-23
I use TUNAPIE for radio & tv.......if you google ' streaming radio' you'll find a slew of apps..some will work in linux

---

### Post by nutz on 2007-07-23
> **candtalan said:**
> How sure are you that the suggestion for bbc radio will not work for your own needs? 
BBC requires realplayer  streams to be used. It is probably a typical example of any station using realplayer streams.


+1

---

### Post by oldos2er on 2007-07-23
>Can someone tell me how to install Real Player in Ubuntu 7.04?

 Open a terminal (command line), cd to the directory where you downloaded the realplayer .bin file. then run:

 chmod a+x RealPlayer10GOLD.bin 
(this makes it executable).

 Then you can run the file:

./RealPlayer10GOLD.bin 

 This should start the installation.

Hope this helps!

---

### Post by wudze on 2007-07-24
well my first day on the forum, and, my first post.:)

I'd really like to thank "candtalan" for the answer to my problem with RealPlayer, the steps that were outlined now allow me to listen to [www.bbc.co.uk/radio](www.bbc.co.uk/radio) directly.  I could not get any sound at all not even with realplayer "standalone".  I had been battling with this for a few days, trying all of the suggested installs, including Helix and making sure that the files were also in the "plugins" directory.I'd downloaded and installed streamtuner and associated files, etc. all to no avail.  I followed the setup as described by "candtalan" and every thing workred the way I thought that it should, thank you once again.

---

