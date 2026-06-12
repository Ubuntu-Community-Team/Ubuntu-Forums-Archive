---
title: "Torrent clients"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Joenash on 2007-08-24
Hi, I have been suffering for two days trying to install a torrent client, 
finally after having to install python 2.4, and build-essential i could run

bittorrent_5.0.8_python2.4.deb 

the Bittorrent deb package runs alright, after which nothing happens and i canot find it in 
Applications > Network 

Is there anything I am missing ? 


Thanks for your help

---

### Post by orange2k on 2007-08-24
Feisty comes with bittorrent client preinstalled, but its not listed in any menu. It just starts when you open a torrent file. But if you want more control over torrent downloads, I recommend Deluge. Its very light on the CPU, but gives you all the control and overview youll ever need...
I dont think its available in the repositories, but there is a .deb package for Feisty on Deluge web page...:)

---

### Post by Ryan3 on 2007-08-24
> **orange2k said:**
> I recommend Deluge. Its very light on the CPU, but gives you all the control and overview youll ever need...
I dont think its available in the repositories, but there is a .deb package for Feisty on Deluge web page...:)
Which is here, [http://deluge-torrent.org/downloads](http://deluge-torrent.org/downloads)

I recently switched from Azureus, which would often get disconnected from the swarms, to Deluge and it's been a good experience so far.

---

### Post by daverich on 2007-08-24
another bump for deluge here.

My ISP throttles torrents and bittorrent is lucky to reach 15kbs, Deluge on the other hand will reach 500-600kbs no problem because it encrypts the files ;)

Kind regards

Dave Rich

---

### Post by hyper_ch on 2007-08-24
I used ktorrent but now I prefer a terminal client - in my case: rtorrent.

---

### Post by Joenash on 2007-08-24
Thanks alot every body 

got deluge , installed and now...........downloading :popcorn:

---

### Post by anaconda on 2007-08-24
ktorrent is also wery good.

With me deluge almost prevents surfing at the same time than downloading torrents. Even if the torrent wont download very fast ....

---

### Post by Kubunteando on 2007-08-24
Another vote for Ktorrent.

It can run in background without noticing it. You can surf the web, write documents, and even play games, at the same time. I can play Doom 3 and download with ktorrent at the same time, and I have a Pentium Mobile st 2GHz.

And of course, it has lot of features.

---

### Post by hyper_ch on 2007-08-24
rTorrent, as a command line torrent client, uses way less ressuorces than ktorrent or deluge or azureus ;)

---

### Post by Ryan3 on 2007-08-24
> **anaconda said:**
> With me deluge almost prevents surfing at the same time than downloading torrents. Even if the torrent wont download very fast ....
Maybe you have too many torrents going at the same time?  Try changing max simultaneous torrents to 1 or 2 (the default is 8, yikes) and set max upload speed to about 2/3 of your upload bandwidth.

---

