---
title: "Unwanted connections?!"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by squidward_tentacles on 2006-06-02
OK, Im sure this is a total noob question, but I cannot dissconnect whatever is connected at port 443. Ive tried,
sudo fuser -v 443/tcp <no result> &
sudo fuser -vk 443/tcp <also with no results>
My understanding is that these and <another connection I cant seem to get rid of  running on 9001>, are all associated with tor. My questionable firewall connections are listed as;

192.168.1.100  18.244.0.144  443  HTTPS
192.168.1.100  222.94.11.129 443 HTTPS
192.168.1.100  213.113.27.69 9001 Unknown

none of these connections are listed as tor, in the program colum of firestarter, and despite everything Ive tried I cant get rid of them <plays creppy music>....Ive tried "sudo killall tor", locking the firewall, rebooting and even editing iptables; "sudo iptables -A INPUT -s 213.113.27.69 -j DROP" for each of the connects, and STILL they are there glaring at me with unspoken menance....can anyone confirm this is normal, or if not how to close these connections, and what they might be doing there? It would be a great burden off my mind, Thanks!

---

### Post by johnc4510 on 2006-06-02
After googling tor, it looks like it is associated with instant messaging and possibly rss feeds. Do you have any of those running?

---

### Post by squidward_tentacles on 2006-06-02
No IM clients besides Gaim,<not running> and its set up to tor as well, when I start gaim I get the usual list of new tor connections....I dont subscibe to any type of RSS feeds either....Theses connections in question appeared abput 3 days ago and havent left since....:confused:

---

### Post by Jimmey on 2006-06-02
If you're worried, security wise, about this, then I can suggest a test using nmap.

nmap's available in the universe respository:>  sudo apt-get install nmap

Then, after figuring your IP ( usually achievable by use of the "ifconfig" command ), you can run a test on your own PC, like this: 
> nmap 000.000.000.000, replacing the zeros with your IP address. This will show you what ports are open on your machine, highlighting any security risks. 

If you find an open port that you've not yourself specifically opened, I'll be suprised. If not, you can rest easily in the knowledge that that connection probably isn't important.

---

### Post by squidward_tentacles on 2006-06-02
Well, thanks for the reply, but Ive already nmaped myself, on both the outer, and inner IP's. Externally, I have no ports open, and internally:
25/tcp    open  smtp
631/tcp   open  ipp
32771/tcp open  sometimes-rpc5 

I have reserched the matter further and from the best I can tell, <and bear in mind this is my admitadly dim understanding of it all,heh;) > these all seem to be broken/ not responding/ <hopefully not rouge, lol> tor nodes, or more appropriately, tor server list providers, that the program checks in order to obtain a fresh list of tor proxys......

18.244.0.144 = Massachusetts Institute of Technology
222.212.53.68 = [CHINANET-SC] Unresponsive <--FROM TOR NETWORK STATUS>
213.113.27.69 =   [ c-451b71d5.026-20-6b6c6d11.cust.bredbandsbolaget.se ] 
This one im really not too sure about......

My question is why CANT I break these connections:confused: 
I have even uninstalled and reinstalled , via sudo apt-get remove tor privoxy, and STILL the connections remain there to thwart me, I would have thought that editing iptables to disallow traffic from these hosts would surely have taken care of it.....If anyone can suggest a way to break these connections/ and or confirm my theory here, PLEASE post](*,)

---

### Post by squidward_tentacles on 2006-06-03
Well, I managed to break the connections by shutting down all machines on the network, unplugging the router, and modem....I still have no idea as to why the connections were "held" though....

---

