---
title: "Help Installing Deluge - Tor configuration"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-01-04
I was installing deluge from a .deb file and as it was attempting to configure it I got an error message. I went through the terminal that said what was occuring and found out that the problem was that I was installing Deluge as root (I assume) and that Tor was installed under my username. It doesn't seem I can copy and paste from there so I cannot give you an exact quote. Is it possible to either make this install with Tor as is under my username or can I make Tor accesible to root so that the installation goes well?

---

### Post by approaching on 2008-01-04
from what i am seeing in a quick not really all that in depth search. tor is a seperate application that just alters the way you use the internet. and that has nothing to do with deluge. all i am trying to get at is that deluge is in synaptic, and there isn't a need to install the .deb by hand like you are doing. unless of course you have some special package that has tor built in to it. if it is would you mind pming me the link?

---

### Post by intense.ego on 2008-01-04
I tried "sudo apt-get install deluge" and it didn't work so I just figured it wasn't in the repos. Perhaps it is under "deluge-torrent" or something else. If you know could you let me know?

---

### Post by intense.ego on 2008-01-05
bump, anyone?

---

### Post by bumanie on 2008-01-05
If using feisty fawn, to install deluge copy and paste the following in to terminal (one long command)

wget [http://download.deluge-torrent.org/ubuntu/feisty/0.5.5/deluge-torrent_0.5.5-1_i386.deb](http://download.deluge-torrent.org/ubuntu/feisty/0.5.5/deluge-torrent_0.5.5-1_i386.deb) && \
sudo apt-get install libboost-date-time1.33.1 libboost-filesystem1.33.1 libboost-thread1.33.1 && \
sudo dpkg -i deluge-torrent_0.5.5-1_i386.deb && \
rm  deluge-torrent_0.5.5-1_i386.deb

If you are using gutsy gibbon go to the deluge website and download the gutsy package from there, apparently the synaptic package in gutsy has bugs.
I don't think you can operate deluge through tor. There is a blocklist loader that can be configured within deluge.

---

### Post by aktiwers on 2008-01-05
yeah its called deluge-torrent in the repos. Always try to hid the "tab" key when you are not sure about the app name :)

---

### Post by intense.ego on 2008-01-05
After installing deluge and trying it out with some torrents, I have to say that I prefer KTorrent, despite it being somewhat of a resource hog. Ktorrent just has so many more features than Deluge. Sorry if I wasted your time.

---

### Post by mrthundercleese4 on 2008-01-16
I install the first packet and the second one pops up and says only one software management tool is allowed to run at the same time. any ideas how to get past this? BTW i got the new version off the site.

---

### Post by aktiwers on 2008-01-16
Close Synaptics or Update manager. You cant apt-get stuff while those are running

---

