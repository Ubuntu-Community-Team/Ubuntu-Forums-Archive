---
title: "bit torrent problem"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Quinn The Eskimo on 2007-06-08
ok i'm stuck...
i've been running ubuntu fiesty for a month or so and love it, but i can't get bit torrents to run right. every time i start downloading a torrent it flys for a few minutes and then trickles down to almost nothing. i've tried all the clients and i'm currently using ktorrent trying to download a file and when i start it it is at 100+ kb/s and within minutes it's at .02kb/s but still uploading at incredible speeds. i've changed ports and capped uploads and i don't know whats wrong. i'm using a gateway 507gr and i'm pretty sure i have everything installed right, plus i'm running beyrl, but torrents do the same thing if i uninstall it.

---

### Post by chicoicho on 2007-06-08
Just install Azureus with java and go download torrent. :popcorn:

---

### Post by rich.bradshaw on 2007-06-08
Probably your ISP throttling bittorrent.

---

### Post by croto on 2007-06-08
What are your ISP upload and download max rates? Cap the upload to 70-80% of the max upload rate, that might help. 
Does all internet access get slow or just bittorrent? If everything gets slow, it may be that you have too many connections and that's killing your router. Try limiting it to 100. If it's just bittorrent, it could possibly be what the previous poster suggested...

---

### Post by Quinn The Eskimo on 2007-06-08
i've tried azureus, it was the slowest of several programs i've tried
my isp is timewarner and i just moved, it was the same problem at the old place as here
i'm averaging upload speeds of over 100kb/s and averaging download speed of 0.2kb/s
my roomate is about 100kb/s downloads with windows on the same torrent
i've played around with the max uploads and downloads and have no idea what port things should be but i've googled the net and ran searches on here and tried tons of different ports and get the same results. 
it immediately starts off flying and within 5 minutes drops down to next to nothing
has anyone seen and fixed this problem before?

---

### Post by Mr-Bridger on 2007-06-08
I found the best solution for bittorrent in Ubuntu was to install Wine and then use Utorrent

Works a treat, never liked azerus when i tried it on windows and Ktorrent is not allowed by some trackers

---

### Post by kelvin spratt on 2007-06-08
I use Ktorrent and i get incredible speeds i cap the upload to as low as possible and use dht. But you must remember that a lot of downloads are very slow especially the latest one as their could be hundereds of other people also downloading as well as you and only one seed, one seed 200 leechers [you are a leecher till you hit 100%] = one very slowdownload. If you are being throttled you won't ever be able to reach speed over about 25kps. but you say they start ok over 100kps, try using this as your listening port 61401 and enable DHT. if you are using a router it will need to be set up. [http://portforward.com/routers.htm](http://portforward.com/routers.htm) this will give you step by step instuctions for most routers and applications Ktorrent works with Ktor i the router.

---

### Post by rickycodie on 2007-06-08
it might be your isp killing your download, some of them don't allow file sharing. try to go to the preferences and encrypting the download. that will stop 'em.

---

### Post by Quinn The Eskimo on 2007-06-08
> **kelvin spratt said:**
> I use Ktorrent and i get incredible speeds i cap the upload to as low as possible and use dht. But you must remember that a lot of downloads are very slow especially the latest one as their could be hundereds of other people also downloading as well as you and only one seed, one seed 200 leechers [you are a leecher till you hit 100%] = one very slowdownload. If you are being throttled you won't ever be able to reach speed over about 25kps. but you say they start ok over 100kps, try using this as your listening port 61401 and enable DHT. if you are using a router it will need to be set up. [http://portforward.com/routers.htm](http://portforward.com/routers.htm) this will give you step by step instuctions for most routers and applications Ktorrent works with Ktor i the router.

thanks... i still can't get this to work...
i would assume that since there is a computer in the other room downloading the same torrent at lightning speeds that it's not our isp or the torrent. i saw a couple of things on ktorrents forum about slow downloads and tried them and still nothing. i'm gonna have to try using wine w/ utorrent because i never had any problems on windows with torrents

thanks again everybody
i have to say this is a great community. i've had little conflicts here and there in the month or so since install and i can always find the answer with a quick search or by starting a thread. ubuntu rocks!

---

