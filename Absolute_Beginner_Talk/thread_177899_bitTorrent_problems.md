---
title: "bitTorrent problems"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by luca00i on 2006-05-17
i am having a problem getting my torrents to start.  i have tried to download them with azureus, bitTornado, and the default GNOME client.  all of the progrmas act like they are connected to peers and downloading but never actually download any information.  the status just sits at 0% for ever.  any help for this newbie would be greatly appreciated.  thanks in advance.

---

### Post by it.henrik on 2006-05-17
You will find lots of information about the status of your connection in Azureus. I do however recommend that you go to their homepage and wiki to find out more. 

In azureus you will have 3 "lamps" in the bottom list that are indicating the status of your bittorrent-availability. The most important one is the one in the middle. This one should be green. If not then you are behind a NAT or firewall that doesnt work with uPNP, then you should open and port-forward the port you have told Azureus to use. There is also a column called "health" in the main window that indicates how your torrent is feeling :) you want it to be green. Just hoover your mouse over it to get some info about it. And finaly .. there is another column called "Tracker Status" .. and this one should be ok. 

And then of course .. you might have choosen to dl a torrent with no other peers in the swarm .. and then there is nothing to dl :) If all of the above is OK then you can have a look at the columns called "Seeds" and "peers". Seeds indicate how many others who are sharing the complete file and peers shows how many that are currently trying to dl this file.

There is a lot to learn about bittorrent.. it is a pretty cleaver but a bit complicated filesharing protocol :)

As I said before .. Azureus homepage is the best place to start .. have alook in their FAQ and wiki-pages. There are also forums...

---

### Post by Resurrection on 2006-05-17
Bittornado is even easier.  You should be able to click on the status light in the top right corner and it will give you a pop-up that shows the different colors of the light and what they mean.  It sounds like you may need to forward your ports if you are using a router or gateway.

If you do need to forward your ports your best place to start is:
[http://www.portforward.com/]("http://www.portforward.com/")

I also recommend reading up on Port Forwarding on wikipedia:
[http://en.wikipedia.org/wiki/Port_forwarding]("http://en.wikipedia.org/wiki/Port_forwarding")

I don't know if you will need to tweak iptables for torrents or not.  My main experience with torrents is on Windows based machines, my Linux torrent experience is much more limited.

Another trick you can try is to put your router (again if you are using one) in the DMZ and see if your torrents start working.  Also make sure that no firewall software is blocking the ports that you have your torrent clients set to  use.

---

### Post by Mookawaka on 2006-05-30
I am having the same problem with the default Gnome Bittorrent client.
If this is an issue with port forwarding where do you change the port settings in that program?
When I open the client from the drop down menu I just get a file manager looking for meta files.  When the program is opened automatically by starting a torrent download through firefox I have the same problem as the original poster of not starting any exchange of data and then timing out.
I have some experience with bittorrent and port forwarding but it was in Windoze and with the original Bittorrent by Mr. Cohen.  Would I be better served downloading that client and dumping the Gnome default?

---

