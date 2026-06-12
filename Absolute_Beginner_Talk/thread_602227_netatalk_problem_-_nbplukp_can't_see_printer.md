---
title: "netatalk problem - nbplukp can't see printer"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by BobBlec on 2007-11-04
Greetings,
I'm trying to add my linux machine - a Compaq Presario 5310US running 7.04 - to my AppleTalk setup on my Mac.

My Blue & White Mac (with a G4/500 MHz upgrade) is running OSX 10.3.9. I have my linux machine on an Ethernet LAN; it's sharing my Mac's Internet connection already (points to the Mac's IP rather than the DSL modem's). For a printer, I have an Apple LaserWriter 4/600 PS (named 'Zenger') hooked into the LAN via an old Dayna EtherPrint bridge. It works fine printing from my Mac, but not from the linux machine.

I installed netatalk the way that [https://help.ubuntu.com/community/AppleTalk](https://help.ubuntu.com/community/AppleTalk) said to; when I ran nbplkup, I got this result:

rfblec@ubuntu:/$ nbplkup
ubuntu : AFPServer 65280.93:128
ubuntu : netatalk 65280.93:4
ubuntu : Workstation 65280.93:4
SmurfTower : Darwin 65445.180:128

So netatalk is seeing the Mac (SmurfTower), but *not* the printer!

On the Mac, I have Printer Sharing (System Preferences -> Sharing -> Services) and 'Share my printers with other computers' (System Preferences -> Hardware -> Print & Fax) enabled, which *should* be everything I need.

So how do I get the linux machine to see my printer?

Thanks!

-Bob

---

### Post by SpiritIsReality on 2007-11-04
howdy
any help here?
[http://www.google.ca/search?hl=en&q=share+%22mac+printer%22+site%3Aubuntuforums.org&as_qdr=m3&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=share+%22mac+printer%22+site%3Aubuntuforums.org&as_qdr=m3&btnG=Search&meta=)

[http://www.google.ca/search?as_q=share+mac+printer&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=share+mac+printer&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
trails

---

### Post by BobBlec on 2007-11-05
> **SpiritIsReality said:**
> howdy
any help here?
[http://www.google.ca/search?hl=en&q=share+%22mac+printer%22+site%3Aubuntuforums.org&as_qdr=m3&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=share+%22mac+printer%22+site%3Aubuntuforums.org&as_qdr=m3&btnG=Search&meta=)

[http://www.google.ca/search?as_q=share+mac+printer&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=share+mac+printer&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
trails

SpiritIsReality,
  Unfortunately, no, at least not yet...  :-(

  The sticking point here is that netatalk is seeing the Mac (SmurfTower), but *not* the printer or AppleTalk -> Ethernet bridge.

  Thanks for the links, though!  :-)

  =Bob

---

### Post by Cheesehead on 2008-06-08
My ancient Dayna EtherWrite localtalk-to-ethernet bridge simply cannot be seen from the network by my MacBook or Linux boxes...unless I put a cheap ethernet hub in front of it.

Yeah, an extra hub between my router and my bridge. I can plug the computers anywhere on the network (router or hub). I have no idea why I need the hub, but I really do.

---

