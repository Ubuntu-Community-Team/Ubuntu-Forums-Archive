---
title: "torrent"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ceezax on 2007-03-21
hi there 

i just downloaded the bit torrent from add and remove programmes so i want to run it 

right now ?? where i can find it ??

by the way ?? where the default place for all the downloaded applications from add/remove programmes ???



another question , i want to run media player files so what's the one should i download to run movies ?? and where i can find it ??

---

### Post by nescontroller on 2007-03-21
I would suggest running it with a client... The one I recommend is Deluge. To install it do the following:
1. Copy and paste the following into console:
> sudo apt-get install python-all-dev python-all python-support libboost-dev libboost-thread-dev libboost-date-time-dev libboost-filesystem-dev libboost-serialization-dev libboost-program-options-dev libboost-regex-dev zlib1g-dev
2. Download [Deluge]("http://deluge-torrent.org/downloads/deluge-0.5.0.tar.gz")
3. Extract it.
4. cd /to/whatever directory you put it in.
5. python setup.py build
6. sudo python setup.py install
7. You should get no errors and now everytime you want to use bittorrent go to: 
Applications->Internet->Deluge

---

### Post by fakie_flip on 2007-03-21
> **ceezax said:**
> hi there 
another question , i want to run media player files so what's the one should i download to run movies ?? and where i can find it ??

I suggest replacing totem-gstreamer with totem-xine for movies because it supports many more formats. You can use Synaptic Package Manager to do that. Otherwise you should use Mplayer. For audio I use Amarok and Xmms.

---

### Post by moore.bryan on 2007-03-21
> **nescontroller said:**
> To install it do the following:
1. Copy and paste the following into console:
*total preference-thing, but ```
sudo aptitude install --with-recommends deluge
``` might be simpler...*

---

### Post by Hallvor on 2007-03-21
> **ceezax said:**
> hi there 

i just downloaded the bit torrent from add and remove programmes so i want to run it 


You don`t have to find it. It will launch when you click on a .torrent-file and will work just fine. However, if you want a bittorrent-client with a good GUI (and more CPU-consuming) you should try Azureus. You`ll find it under add/remove programmes.

Edit: I use Bittornado myself. I like the small and lightweight applications, and don`t really need a fancy GUI.

---

### Post by fakie_flip on 2007-03-21
I use Ktorrent and Bittornado. That Deluge torrent client looks nice though. I am going to try it when I get home. I hate Azerus!

---

### Post by moore.bryan on 2007-03-21
> **fakie_flip said:**
> I use Ktorrent and Bittornado. That Deluge torrent client looks nice though. I am going to try it when I get home. I hate Azerus!
[I]i just recently dumped bittornado for ktorrent because i was getting MUCH faster speeds with ktorrent...
and i, too, hate azureus.
[/I]

---

### Post by Hallvor on 2007-03-21
That is very strange. I experimented with several clients in Windows, and the performance between them were notable. However, I believe it had more to do with the default tweaking than anything else.

Personally, I have downloaded at more than 1100 kb/s on Bittornado, so it is not "slow" at all.

---

### Post by belikralj on 2007-03-21
[QUOTE=ceezax;2333144]hi there 

i just downloaded the bit torrent from add and remove programmes so i want to run it 

right now ?? where i can find it ??

by the way ?? where the default place for all the downloaded applications from add/remove programmes ???
]

You can find your bittorrent in your Applications -> Internet menu
But first you need to unhide it. Go to System -> Preferences -> Menu Layout

in the lefthand menu select Internet submenu and then tick the bittorrent box which should be unticked if you can't find it.

The default place is in your Applications menu in the appropriate submenu but not all of them appear right away. Like bittorrent you must unhide them.

Hope this was what you were after
:)

---

### Post by moore.bryan on 2007-03-21
> **Hallvor said:**
> downloaded at more than 1100 kb/s on Bittornado,
*i never got close to that number with bittornado, but now i always lingering around 1.5mbs*

---

### Post by dorcssa on 2007-03-21
> **nescontroller said:**
> I would suggest running it with a client... The one I recommend is Deluge. To install it do the following:
1. Copy and paste the following into console:

2. Download [Deluge]("http://deluge-torrent.org/downloads/deluge-0.5.0.tar.gz")
3. Extract it.
4. cd /to/whatever directory you put it in.
5. python setup.py build
6. sudo python setup.py install
7. You should get no errors and now everytime you want to use bittorrent go to: 
Applications->Internet->Deluge
It can be done in dapper too? Cos I have problems with installing the newest deb on dapper. It's the source way, right? And after this, how can I remove it? I guess it won't be updated automatically.

---

### Post by Hallvor on 2007-03-21
> **moore.bryan said:**
> *i never got close to that number with bittornado, but now i always lingering around 1.5mbs*

Good for you. :) Torrents seem a lot faster on Ubuntu than on Windows. Is that your experience too?  Never got more than 200-300 kb/s on Windows even if there were plenty of seeds.

---

### Post by fakie_flip on 2007-03-21
> **moore.bryan said:**
> [I]i just recently dumped bittornado for ktorrent because i was getting MUCH faster speeds with ktorrent...
and i, too, hate azureus.
[/I]

There are some settings you have to change in Bittornado to tell it to use ports 6881-6999, otherwise it will use random ports. You must also have the tcp ports port forwarded if you have a router and not blocked by a firewall for the best results. I thought all torrent clients used those ports by default, but I found out Bittornado doesn't.

---

### Post by moore.bryan on 2007-03-21
> **Hallvor said:**
> Good for you. :) Torrents seem a lot faster on Ubuntu than on Windows. Is that your experience too?  Never got more than 200-300 kb/s on Windows even if there were plenty of seeds.
*same hear.  add it to the list of reasons why windows sucks...*

---

### Post by moore.bryan on 2007-03-21
> **fakie_flip said:**
> There are some settings you have to change in Bittornado to tell it to use ports 6881-6999, otherwise it will use random ports. You must also have the tcp ports port forwarded if you have a router and not blocked by a firewall for the best results. I thought all torrent clients used those ports by default, but I found out Bittornado doesn't.
*i used a different set of ports because the other range is where a large sibling looks, forwarded everything, and allowed the ports; just wouldn't play nice for me.  :-)*

---

### Post by fakie_flip on 2007-03-21
There is a thread about disabling ipv6 to make your internet in Ubuntu faster. Mine seems to be faster after doing it. You can search for the thread if you want to read it. The way to disable ipv6 is by blacklisting, preventing the module to load. Add "blacklist ipv6" to /etc/modprobe.d/blacklist. Doing "lsmod | grep ipv6" will probably show that the module is loaded. Reboot and do that command again. It should not be loaded anymore. I've also blacklisted some other modules such as floppy sense my computer does not have a floppy and bluetooth sense I do not use that either.

---

