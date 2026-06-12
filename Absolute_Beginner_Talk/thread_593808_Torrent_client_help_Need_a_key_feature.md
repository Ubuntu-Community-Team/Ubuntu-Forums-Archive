---
title: "Torrent client help: Need a key feature"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by oxymoron on 2007-10-27
lo,

I have finally took the plunge and deleted my Windows partition and have had a successful time with Ubuntu 7.10 amd64 so far. The only thing that is bugging me atm is (you guessed it) torrent clients!

I need one that can do the following::


1)  Ability to select which file you want to download 1st and leave the second part till later. I used Bitlord in Windows and that had the ability for me to select which videos of the torrent I downloaded first. e.g. I could  download homevid1.avi and not download homevid2.avi even if they were in the same torrent.

2) Would be good if the [INSERT LINUX CLIENT NAME HERE] Could read if I had imported a partially downladed torrent file from my old Windows OS and start pick up the download. I tried to do this with Deluge and it started downloading from 0%. This again worked fine in Bitlord when I had Windows.

Can anyone help?

Is it just best to use Bitlord with Wine?

---

### Post by sneezymelon on 2007-10-27
use ktorrent. it's the best one in the world

---

### Post by Pumalite on 2007-10-27
Ktorrent works fine for me.

---

### Post by dljesse on 2007-10-27
I personally prefer running utorrent with wine, works great.

---

### Post by Fred_E _krugar on 2007-10-27
+1 for Ktorrent

---

### Post by oxymoron on 2007-10-27
yay KTorrent can solve my point 1) :D. Now gonna see if it solves point 2 :D

---

### Post by raycosm on 2007-10-27
Another vote for Ktorrent, although for some reason it's always been a bit iffy for me whenever I use it in GNOME. It should work fine for most people though.

---

### Post by DeepNoob on 2007-10-27
I run utorrent in Wine.  Excellent.

---

### Post by kostkon on 2007-10-27
*Deluge* is also a good torrent client.

---

### Post by thelocust on 2007-10-27
[COLOR=#000000][FONT=Times New Roman][SIZE=3]I believe that there is an “[/SIZE][/FONT][COLOR=black][FONT=Tahoma]import existing download(s)” option in one of the menus. Sorry I’m at work can somebody confirm this.[/FONT][/COLOR][/COLOR]

---

### Post by digger95 on 2007-10-27
Another vote for KTorrent here.  Yes it has all the features you asked about.

1.  There is a files tab where you can check/uncheck which files in a particular torrrent you want to download (or not).  You can also right-click the files within a torrent and choose which one you want to download first, last, etc.  So if there are multiple videos within a torrent, you can choose which one to download first.

2.  KTorrent has the ability to 'import existing download under the file menu.  You just need to configure that option first in your settings menu.  A window opens up asking you where the .torrent file is located, and also where the download folder is for the partial file.

I get great speeds with KTorrent.  Use a linux app and spare yourself the wine  :)

Dig

---

### Post by cyneuron on 2007-10-27
Deluge is THE BEST TORRENT CLIENT for Ubuntu, especially you are a GNOME user (because Ktorrent needs KDE libs to install and run, which makes it heacy when using it on GNOME)...

also download speeds with Ktorrent are fluctuating....u never get full speed wit ktorrent....


Deluge has all feature ou requested, its developing very fast, awesome feature are introduced with every update.....its really light weight...gives you max speed you connection can have....has best encryption algorithms available today....

it was only the torrent client which was stopping me to switch to ubuntu completley, now Deluge has solved this problem....

i am sure Deluge will even beat utorrent on windows one day in terms of features....

to install simply search for deluge in synaptic package manager....

---

### Post by thelocust on 2007-10-27
> **cyneuron said:**
> also download speeds with Ktorrent are fluctuating....u never get full speed wit ktorrent....
Them's fighten words.

---

### Post by digger95 on 2007-10-27
Of course there's nothing to prevent you from trying several different clients to see which one you like best.  Ubuntu's package management makes it pretty easy.  I've tried both Deluge and KTorrent and they are both good.  I prefer KTorrent though because I'm a KDE guy.  Be sure to have backups of your partially downloaded files, in case the import goes horribly awry the first time.

---

### Post by DeepNoob on 2007-10-27
"Use a linux app and spare yourself the wine"

I gave Ktorrent a ride.  It worked just fine with torrents from Demonoid, but every single torrent I tried from TPB kept "stalling".  It refused to connect to seeders.  Went to their forums to look for help but couldn't find a way to configure it properly, so I gave up.

But if you have any suggestions digger, I'll certainly give it another try.

---

### Post by markharding557 on 2007-10-27
you could try azureus

---

### Post by sloggerkhan on 2007-10-27
Deluge.

[http://deluge-torrent.org/News:Portal](http://deluge-torrent.org/News:Portal)

---

### Post by oxymoron on 2007-10-28
Thanks for you posts guides. I have tried both Deluge & KTorrent and it seems KTorrent has more features, but Deluge has faster download speeds.

I guess Ill have to use both to meet all my needs until Deluge matures & gets more features

---

### Post by sloggerkhan on 2007-10-28
I figure you looked though the plugins available for deluge?

---

### Post by daimaru on 2007-10-28
> **markharding557 said:**
> you could try azureus

yes i agree i love azureus ( dont love the vuze interface though ) but it can do all you asked for .

---

### Post by Leonivek on 2007-10-28
I love Azureus also, but I've had sporadic issues with it in Ubuntu in the past, and I kinda find it bloated.

Deluge gives you the option of selecting which files to download.  Look through the plugins... I can't remember which it is and I'm at work on Windoze so I can't check.   I think it's the one that adds the "Files" tab to your torrent details, not sure. 

Deluge also impressed me BIG TIME by how fast my downloads are compared to all the other clients I've tried... not sure why they are much faster with Deluge than any other client, but it is noticeably so.  And here I thought it was my ISP's throttling.

---

### Post by cyneuron on 2007-10-29
i bet Deluge will defintely be selected for default torrent client in Ubuntu in next release....its so like Ubuntu....simple yet powerful.....and it just works awesome.....and above all it is based on gtk.....not like ktorrent with full of feature, but with fluctuating download speed.....

---

### Post by hyper_ch on 2007-10-29
with rtorrent both can be done easily (plus it is a command line client so you can easily control it from everywhere where you can ssh into your box)

---

### Post by badguyanil on 2007-10-29
azureus is my choice. Had been using it in windowws and Vuze 3 in linux is giving me very good speeds.The added advantage of it need not be installed. Just unzip and run!

---

### Post by stomponthis on 2007-10-29
> **sloggerkhan said:**
> I figure you looked though the plugins available for deluge?

Yeah another Deluge fan!
Some of the plugins are a must

---

### Post by badguyanil on 2007-10-29
> **stomponthis said:**
> Yeah another Deluge fan!
Some of the plugins are a must

I have used Deluge too. what plugins are available for Deluge? where do i find them and how do i install them.

---

### Post by stomponthis on 2007-10-29
> **badguyanil said:**
> I have used Deluge too. what plugins are available for Deluge? where do i find them and how do i install them.

Just open Deluge - Edit - plugins
or there is a plugins icon on the bar thingy!
Just tick whatever plugin you want and it magically appears!

I use 
Blocklist - blocks IP's
Scheduler - schedule!
Torrent Files - select certain files within a torrent to download

Am waiting for a torrent release for a specific user to try the RSS plugin!

---

### Post by Angus77 on 2007-10-29
I had nothing but problems with KTorrent and Azureus. I got uTorrent working, but I had some weird glitches with it. It seems to work better since I upgraded to Gutsy.

I use **Deluge** now, though. Never had the slightest problem with it.

---

