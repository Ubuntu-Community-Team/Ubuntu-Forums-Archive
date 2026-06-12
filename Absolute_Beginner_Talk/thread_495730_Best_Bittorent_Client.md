---
title: "Best Bittorent Client?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-07-08
I was just wondering what you guys would consider the best bittorrent client for linux? Thanks :popcorn:

---

### Post by Littleweseth on 2007-07-08
I use rtorrent, which is an ncurses text-interface app. It's fast, and has a very small footprint.

I've heard good things about KTorrent - apparently, it's the utorrent of the linux world.

Avoid Azureus like the plague. :)

-lws

---

### Post by Eggnog on 2007-07-08
I tried a few out when I first installed Feisty.  Azureus gave me nothing but fits so I dumped it.  I used uTorrent in XP and heard it ran well under Wine, but then I found Ktorrent and it's just what the doctor ordered for me.  It reminded me enough of uTorrent that I decided not to mess with Wine and uTorrent.

---

### Post by InQuieto on 2007-07-08
I like azureus, but it's so heavy and installation is difficult (i wrote an howto on my [blog]("http://inquiete.wordpress.com/2007/05/12/una-spina-nel-fianco-azureus-e-ubuntu-feisty/"), in italian, or you can take a look at the ubuntuwiki). I prefer anyway Deluge, the new release (0.5.2) it's very fast and complete, almost like azureus. 

Ktorrent in a gnome enviroment is orrible (but it's a good client, anyway).

With all of those possibilities, i don't see why use utorrent on wine.

---

### Post by davidjmayo on 2007-07-08
another vote for ktorrent 
but I usually use kubuntu

---

### Post by pyros on 2007-07-08
I usually just use the default client, unless it has a problem finding a tracker or... well, any problems for that matter. In that event, the 10 kiloton bittorrent solution called azureus gets the job done.

---

### Post by SlackLagg on 2007-07-08
I'll put my vote in for Azureus. Yes, there is a bunch of settings to figure out, and installation might leave you scratching your head, but after I got it up and running, I haven't had too many problems. *  Occasionally it will gripe about a firewall, but I just re-run the NAT wizard and it sorts itself out. (and it is Java, so yes, it can suck up resources if you don't have much ram, but any system with 1gb or more shouldn't have a problem. I never had a problem when I still had 512mb) 

I'll also give a tip of the hat to Deluge. as InQuieto said, 0.52 is out now ( [http://www.deluge-torrent.org](http://www.deluge-torrent.org) ) and it's pretty slick. Finds more seeds than previous versions, and seems more stable. Still a couple of bugs such as the torrent file must be named *.torrent for "open with X"  or double click to open to work . It can find non *.torrent named files, you just have to tell it to look for "all file types" after you've open the program and clicked "add torrent" .

Also, not as many options as Azureus,  but as long as you aren't trying seed 10 torrents , with only three active torrents availble at a time, in combination with only the the lowest ratio seeds actually connecting, as well as downloading a torrent, keeping in mind that your download may have a higher ratio than your seeds therefore causing it to be paused until your lower ratio seeds get a better ratio,  you'll be okay (Azureus handles that situation pretty well)  


* the long and short of Azureus installation is you'll need Sun Java, then you'll need to unzip the files to a folder that either you or a group you're a member of has read/write permissions. Then you'll need to make a shell script so you can "open with X" or double click torrents to open in Azureus. After you get that you'll need to setup options, but Azureus has some pretty helpful wiki material with links built into the program.  There are multiple guides around here on it, but most of them neglect that when you're making the shell script, you **may** have to make a If/Else statement depending on the number of files you are choosing to open...okay now I'm just rambling

---

### Post by ugm6hr on 2007-07-08
Another vote for KTorrent.  The UPnP works (if you load the plugin), which makes setting up routers etc dead easy.

But then I use XFCE / Xubuntu, where it looks and works just fine.

---

### Post by erimar77 on 2007-07-08
another vote for ktorrent... even if you're using gnome

---

### Post by HunkieChan on 2007-07-08
i vote for deluge, azureus was good but it sucks now, utorrent is awesome for windows..

---

### Post by atria on 2007-07-08
If you need more features, go for Azureus.

However if you need a smaller and lighter client, perhaps go for Deluge/KTorrent.

I use Azureus personally since i need those extra features, heh.

---

### Post by atria on 2007-07-08
[edit]sorry internet was lagging and double posted.[/edit]

---

### Post by SlackLagg on 2007-07-08
> **atria said:**
> If you need more features, go for Azureus.

However if you need a smaller and lighter client, perhaps go for Deluge/KTorrent.

I use Azureus personally since i need those extra features, heh.


heh, I should have just let you post for me. You pretty much said the same thing I did but in 1/2 the space 	#-o

---

### Post by dfreer on 2007-07-09
I actually really like my torrentflux server using bittornado as a backend, although back when I used bittorrent on my laptop I thought azureus was the only one that worked well, never got to try deluge but I hear it's great for GNOME.

EDIT: not sure if torrentflux counts cuz it's not really a client, but hey it's still awesome!

---

### Post by RomeReactor on 2007-07-09
Hi. I'm surprised no-one gives any votes (or credit) to the bittorrent client that comes by default on Ubuntu; for me, it's simple, lightweight enough, and *very* fast. If I want to simultaneusly download multiple torrents, I usually just use it from the terminal (**btlaunchmanycurses /home/romereactor/Torrents**). I use Azureus every now and then, but it just isn't as fast (or maybe my configuration isn't quite right), and is unnecessarily bloated, in my opinion).

I have to say, though, that Ktorrent is just *awesome*.

---

### Post by hyper_ch on 2007-07-09
I'm using ktorrent on Xubuntu....

However some people I know just run bittorrent because they can command it from the command shell through a ssh connection and don't need vnc for it...

---

### Post by AlexenderReez on 2007-07-09
i vote for azureus .....!!

---

### Post by Gausian on 2007-07-09
Deluge is the best ive come across yet.

I used µtorrent on windows, but was left with Azureus when i went to 100% Linux.  I got tired of it and tried Deluge, and im totally stoked that i found it.

---

### Post by rye_ on 2007-07-09
I vote Deluge too.

---

### Post by coolen on 2007-07-09
I haven't really looked into it too much, but KTorrent seems pretty good.
When I get time, I'll start looking for a good command line client. Torrents aren't as huge priority of mine at the moment.

---

### Post by lbelloq on 2007-07-09
Tried Deluge, KTorrent, Azureus, and the default GNOME client.
KTorrent: Ugly as hell, but fast and stable.
Azureus: Good, but sucks ut way too much resources.
default: Ugly and not intended for multiple downloads.
Deluge: The best so far, consistent with desktop interface, light on resources and fast downloading. Lacks more options, though.

My personal choice is Deluge.

---

### Post by coolen on 2007-07-09
Oh, I tried Azureus. I used BitComet on Windows, and loved it. Azureus was fairly similar on features, but generally, it only lasts a half hour for me. It'll suddenly quit, then I'll have to go and manually start deleting files to get it to open up again for more than two seconds.
Not impossible, but too much work. Also, as mentioned, very heavy on resources.

---

### Post by destructchaos on 2007-07-09
i don't know what all this talk about ktorrent being stable is all about.  it crashes quite regularly, every half hour for me.  it's about to the point where i could set my watch to it.  i finally got tired of messing with it and went back to utorrent on my old windoze box.

---

### Post by Eggnog on 2007-07-09
I'm running Ktorrent under GNOME and have never had a problem with it.  You could try Deluge, I suppose.

---

### Post by darell_m on 2007-07-09
I also vote for Ktorrent with Gnome. I was a utorrent fan before in windows. Also found the upnp worked well with ktorrent with my router where utorrent did not. I had already set up my router for port forwarding (that takes some study) so also did this with Ktorrent as a breeze.  I tested speed using opensource.org download, which maxes you out in a few minutes, and got very similar speed as when using utorrent under windows (to test maxing out your download speed check utorrent setup guides - excellent). Anyway, my opinion

---

### Post by Wiebelhaus on 2007-07-09
Ktorrent is the shizzie..

---

### Post by The Seeker on 2007-07-09
I'm an Azureus user myself. I've found downloading the tarball from the official site and installing manually gives me better performance than using the package found in the repos.

---

### Post by Church.Cameron on 2007-07-09
I will have to say from my exirience with torrent clients, uTorrent gives me the most satifying expirience when using it on linux, good support on it to

---

### Post by fastpakr on 2007-07-09
I also downloaded Azureus from the official site and haven't had a seconds trouble with it (several months now).

---

### Post by Ozeuss on 2007-07-09
ktorrent is great, even though i use gnome. it's very full featured and stable for me.

---

### Post by michaelzap on 2007-07-09
> **Ozeuss said:**
> ktorrent is great, even though i use gnome. it's very full featured and stable for me.

Ditto (the recent update made the interface a lot better, too).

---

### Post by Nythain on 2007-07-09
my vote is for rtorrent... tried all the popular gui clients and had different problems with each, ranging from speed, to lack of options, to constant crashing...

rtorrent is just as powerfull as the most powerfull gui client, supports multiple download, consumes a minimal amount of resources (on my machine i think its like .3 cpu and 4.1 memory... its very stable and reliable... and its not hard to learn how to use (trust me, if i can get it down anyone can)

---

### Post by 1jackjack on 2007-07-09
Hi,
just installed rTorrent, and round that blasted .rTorrent.rc file on the net, and tried configuring a few options, but were not sure on all of them. Did you find any good documentation to get started with rTorrent? I feel a bit lost.

Jack
p.s. Do you HAVE to un-hash all the options in that config file, or only the ones you want to enable? i.e. 
> # The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.nop

---

### Post by sugarland2k on 2007-07-09
I use Ktorrent also and keep my stuff in a TOR folder.  With 6mb DSL it downloads full ISO's quick and painlessly.  But I usually run Kubuntu and try to leave the system alone with big downloads (or CD burns) for the fewest errors ;)

Friends to not let friends run Vista!

---

### Post by Inxsible on 2007-07-09
I am surprised no one has mentioned qBittorrent.

I used Deluge, but couldnt find an option for selective downloads within a torrent, so i went with qBittorrent and it works great !!

---

### Post by Frak on 2007-07-09
1. kTorrent
2. Deluge
3. µTorrent
4. Azureus

---

### Post by josinalvo on 2007-07-17
just to let you guys know, there is a compiled version of azureus in ubuntu. (I mean, one compiled for native machine language, one that does not need to run "over" java)
I did not try it, just passed by it while seeking for a text client
azureus-gcj, if I am not mistaken, is the package name

---

### Post by zerobinary on 2007-07-17
transmission is fast light weight suppport asian character
deluge don't support asian character crash often
azureus and ktorrent sux memory suxer
bittorrent cool when it works sometimes don't work with the tracker
definably transmission

---

