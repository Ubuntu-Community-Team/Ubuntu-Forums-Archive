---
title: "torrent problems."
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-08-10
Facing some download problems with the torrent clients. I connect to internet broadband using pppoeconfig in linux. Using the same torrent client azureous on both windows (xp) and ubuntu. but the speeds of download vary a lot. in windows i get download speeds upto 200kbps+ but in linux it hadly ever crosses 50kbps for the same torrent. also one interesting thing which i have noticed is the ubuntu update packages download at 200kbps+ alright. is it something to do with ports and all coz while installing azureous the port test said alright for th port i am using in both.....any suggestions!!!

---

### Post by cobrn1 on 2007-08-10
Is the port you're using open in ubuntu? If not that might explain the poor speed.

---

### Post by SOULRiDER on 2007-08-10
I think its probably the torrents, youve just had bad luck when using Linux. Also, can i recommend another BT client other than Azureus, its a resource hog.

Check out Deluge Torrent if you use Ubuntu or Xubuntu or Ktorrent if you use Kubuntu. uTorrent works perfectly well uner wine too, so if you used it in windows you can use it here too!

---

### Post by cobrn1 on 2007-08-10
He said it was the same torrent, and while speeds do vary, ubuntu has an inbuilt firewall set to block all ports bty default, and you need you listening port open. How could he chack to see whuch ports are open?

Also, you may want to look into getting a graphical front end for the firewall, like firestarter

---

### Post by amazingtaters on 2007-08-10
> **SOULRiDER said:**
> I think its probably the torrents, youve just had bad luck when using Linux. Also, can i recommend another BT client other than Azureus, its a resource hog.

Check out Deluge Torrent if you use Ubuntu or Xubuntu or Ktorrent if you use Kubuntu. uTorrent works perfectly well uner wine too, so if you used it in windows you can use it here too!

I would advise against utorrent, due to its closed source nature. It troubles me that BitTorrent (the protocol and the official tracker aka utorrent) are closed source. Keep to open source solutions as much as possible.

To check ports first do this...

sudo apt-get install nmap

     THEN

sudo nmap -sS -sV localhost

That will tell you what ports are open.

---

### Post by jackmc on 2007-08-10
delete

---

### Post by lepz on 2007-08-10
> **amazingtaters said:**
> I would advise against utorrent, due to its closed source nature. It troubles me that BitTorrent (the protocol and the official tracker aka utorrent) are closed source. Keep to open source solutions as much as possible.

To check ports first do this...

sudo apt-get install nmap

     THEN

sudo nmap -sS -sV localhost

That will tell you what ports are open.

Do you need to be running a torrent to check this?

---

### Post by houstonbofh on 2007-08-10
It is probably your upload settings.  While transferring, how many people are downloading from you in each?  Bet you find your difference there.  Some good windows programs are just bad linux programs...  Thay are not the same.

---

### Post by amazingtaters on 2007-08-10
> **lepz said:**
> Do you need to be running a torrent to check this?

No you dont need to be running a torrent. Nmap is a programme with a lot of uses, finding open ports being one of them. To get all of the nmap commands just type nmap in console or go here:[http://insecure.org/nmap/man/man-briefoptions.html](http://insecure.org/nmap/man/man-briefoptions.html)

---

### Post by ellgor on 2007-08-10
Hi,

If you are still having trouble, check out Ktorrent, looks pretty similar to utorrent and works just as fast (once the set up has been done i.e it tells you which ports to activate) hope this helps.

Regards, Ellgor.

---

### Post by PhenixRising on 2007-08-11
> **badguyanil said:**
> Facing some download problems with the torrent clients. I connect to internet broadband using pppoeconfig in linux. Using the same torrent client azureous on both windows (xp) and ubuntu. but the speeds of download vary a lot. in windows i get download speeds upto 200kbps+ but in linux it hadly ever crosses 50kbps for the same torrent. also one interesting thing which i have noticed is the ubuntu update packages download at 200kbps+ alright. is it something to do with ports and all coz while installing azureous the port test said alright for th port i am using in both.....any suggestions!!!

I have been having the same problem with Azureus as of late.  I have gone above 100kbs a few times but what I can not figure out is how the file that went above 100kbs only had a few established links while two of my torrents are just sitting idle with multiple connections to seeders and peers.  It is very frustrating.  I've changed ports a couple of times and each time Azureus has said that they are fine.  To add insult to injury Azureus decided to try to download a torrent that I wanted to finish off.  I had 2/3 of the 21 gig file but now I'm back down to under 2 gigs.  Seems it did not want to obey my do not download request.


10 minutes later, I switch to ktorrent and I'm downloading at 900 kbs and sometimes I'm hitting +1,000 but the big file I want is stalled.  Anyway I think Ktorrent's much greater performance over Azureus has something to do with this...

Completed torrent files are typically published on websites or elsewhere, and registered with a tracker. The tracker maintains lists of the clients currently participating in the torrent.[2] Alternatively, in a trackerless system (decentralized tracking) every peer acts as a tracker. This is implemented by the BitTorrent, µTorrent, BitComet and KTorrent clients through the distributed hash table (DHT) method. Azureus also supports a trackerless method which is incompatible (as of April 2007) with the DHT offered by all other supporting clients. (wikipedia)

---

### Post by badguyanil on 2007-08-14
hmm thats a good one...but i have ubuntu with genome desktop environment...is it advisible to install ktorrent...wihich is obviously built for a kde desktop!!!! just inquisitive..
also can you advice something on the port front too... i mean how do i check which ports are open and if needed open a few ports for the torrent clients.... keep the replies coming.. thnx in advance
regards.

Just forgot to mention...am running Azureous for quite some time on my win xp machine..and am more than satisfied by the performance..well i agree it is a memory hog but have never ever had any problem with the files downloaded with that client. utorrent did give some problems with downloading big files such as movies.. some of the bits in the file were missing and the movies were unplayable in Divx players...only thanks to vlc could play them on the comp....anyways if you guys suggest ktorrent will give it a try!

---

### Post by badguyanil on 2007-09-02
OK guys can anybody let me know if lTorrent is advisable on Ubuntu too!!! coz kTorrent clearly mentions it to be for KDE????

---

### Post by SOULRiDER on 2007-09-02
Ktorrent is intended to be used in KDE, you can use it in GNOME but you will need to isntall several dependencies (its automatic but they use Hd space). I suggest you try Deluege if youre uring Ubuntu

---

### Post by badguyanil on 2007-09-02
Hmm thats cool but how do i install Deluege..cant find it in Sympatic????

---

### Post by MozartlovesUbun2 on 2007-09-02
hmm i guess the torrent download speed differs depending on the torrent itself, download a copy of feisty or knoppix and see how fast it comes

just a quick question

is Azureus a good torrent software?

---

### Post by badguyanil on 2007-09-02
Have used Azureus on windows for ages...it does hog the memory(ts java based).. but had no problems in tweaking and makiing it run smooth! Has loads and loads for options to set from. Latest to the addition id Vuze!!! and a colaboration with BBC where customers can directly purchase the telecast and watch.....

Above all it has long been the best torrent client! and i am one satisfied user!

---

### Post by badguyanil on 2007-09-02
but still dono if i shoudl go for azureous in UBUNTU!!! it crawls for some reason!!!!!

---

### Post by badguyanil on 2007-09-05
Well now a different problem with Azu!... i am downloading 2 files from Azu. if i start azu it loads (shows the startup screen) and exits all by itself!!! dono whats the problem! Any help!

---

### Post by punong_bisyonaryo on 2007-10-01
Am now just trying out Deluge. Finally! A client that can download something despite ALL ports in this apartment's broadband being closed! It's made for GNOME, has a simple and clean interface, and it looks very promising.

---

### Post by hyper_ch on 2007-10-01
Deluge can be found on [http://www.getdeb.net](http://www.getdeb.net)

I prefer rTorrent - it's terminal based, so it hardly uses any resources and due to Screen I can ssh into my box anytime and control it without problems.

---

