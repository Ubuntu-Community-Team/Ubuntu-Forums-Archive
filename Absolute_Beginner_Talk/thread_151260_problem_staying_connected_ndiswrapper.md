---
title: "problem staying connected: ndiswrapper"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by Polygon on 2006-03-27
ive had ubuntu installed for a while, but i took a month or so break because of school and such. I changed network cards because we got a new better router, so when i picked up ubuntu again two days ago, i first needed to get my internet working

after searching for the stupid drivers, i finally found them (two copies, version 1.2 WHQL and version 1.1 shipping drivers) and following a page on the ubuntu wiki i got them installed fine

the internet works on ubuntu.... its just randomly my internet stops working and it is a PAIN to get it back working. I usually have to disable/renanable wlan0 in system>admin>networking to get it working again, and even then sometimes it refuses to work =/

ive tried using both copies of the drivers that i found for my  wireless network card,  and i still get disconnected randomly

is it just because the drivers are not all that compatabile with ndiswrapper, or it is some other problem?

[http://www.dlink.com/products/?sec=0&pid=422](http://www.dlink.com/products/?sec=0&pid=422) <-- that is my network card

[http://www.dlink.com/products/support.asp?pid=422&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=422&sec=0#drivers) <-- these are the drivers (both sets) for my network card

I am using ubuntu 5.10.

also remember, im still a n00b at this, so please bear with me ^^
thanks

---

### Post by Polygon on 2006-03-27
bump

---

### Post by RocketMan10404 on 2006-03-28
I'm gonna bump this as well, because I'm having the exact same problem.  I'm at work at the moment, and can't give the exact software versions, but I've been using the newest version of Ndiswrapper, the windows xp driver version recommended for my hardware (Netgear WG111 USB wireless network dongle), and Ubuntu Breezy.

I can install ndiswrapper and configure the network as well as search for networks easily, and everything works great.  However, when I try and actually use the internet, it seems that whenever I get directed to certain servers, the connection just quits.  Scanning for networks reveals none all of a sudden, and I have to remove the USB device from my computer, plug it back in, and re-insert the module as well as reconfigure the settings all over again.

Sometimes the internet will work fine, but usually it's 30 seconds or less.  Also, when it gets hung up when querying a particular server, it seems to *always* stop when querying that server, even after I go through the whole setup process again.

I don't know what's going on, because everyone else I can find with my hardware and my version of ndiswrapper seems to be having no problems.  I'd appreciate any ideas.

---

### Post by Polygon on 2006-03-28
bumped 

please help us out :)

---

### Post by Polygon on 2006-03-28
34 views and not one of them can help me out? come on! why are you guys answering every single post but THIS ONE. Sorry if im sounding rude but i have searched the internet, the ubuntu wiki and even posted here, and still have no help whatsoever -.-

---

### Post by NetMatrix on 2006-03-28
Polygon,


     Here is the ndiswrapper wiki page that has a list of known cards and there issues.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

     Perhaps it is an issue with power management.  I've seen where PCI cards have an issue with power management.

Rocketman,


     If you could post your info that would be helpful.  I would also direct you to the wiki page if you are using ndiswrapper.  The page is in alpha/numeric order.

Hope this helps.

---

### Post by Polygon on 2006-03-28
thanks for the reply, i will check that out later when i get back, and report on my findings

thanks again.... first reply in like a day ;)

---

### Post by Polygon on 2006-03-29
hmm, there is nothing there for my specific card, as its a dlink g520m and all they have there are just g520

but upon looking at the drivers, the .sys file says in the description "driver for atheros ar5005vl wireless network adapter", should i try looking for drivers for that card?

---

### Post by NetMatrix on 2006-03-29
Yeah, I would try searching for that because this is probably the chipset that the card is based on.  However I don't know that the drivers for that specific card would work.

---

### Post by RocketMan10404 on 2006-03-31
Thanks for your response, I appreciate any attempt to tackle this pain in the *** problem.  Unfortunately I'm at work again, and can't grab as many version numbers as possible, but I do have a few handy.

The version of ndiswrapper I'm using is 1.11, compiled from source.  I have the WG111 version 1 USB dongle, and I'm using the new v2.1 drivers from netgears page for it.  I tried the initial driver release (March 15, 2004), but it doesn't work with my hardware.  Also, I'm using the Breezy version of Ubuntu.

The behavior of my system during this problem is very strange.  Certain IP's seem fine, and certain ones seem to halt my internet.  For instance, after I get everything initially configured and working, I can ping [www.google.com](www.google.com) for as long as I want, as many times as I want, with no problems.  However, certain other IP's seem to give me big problems.  I can't think of very many specific ones right now accept for myspace.com.  I can ping google alone for at least 5 to 10 minutes, then as soon as I try to ping myspace.com, the connection stops working and I lose all packets.  The biggest problem is web browsing, where most pages download fine, but the random connects to different servers for banner ads and such usually screws me up at some point, and causes the connection to stop.  And of course, going to myspace.com doesn't work at all, and the same is true for certain other websites.

I can get the connection up and running again, all I have to do is disable my connection, rmmod ndiswrapper, unplug the USB dongle, and then plug it back in and repeat the setup process.  I am not really a linux *newbie* per se, but I posted this issue here because it was related.  The Ubuntu forums here seem to be one of the few places I can find other people having this problem.

If there's any version numbers I've left out, just let me know and I'll post more info when I get home.

---

### Post by NetMatrix on 2006-03-31
Maybe it would be best to remove the version of ndiswrapper that you have currenty and reinstall it from the repositiories.

```
sudo apt-get install ndiswrapper-utils
sudo apt-get install ndisgtk
```

The ndisgtk will give you a GUI interface to install your windows driver.  Perhaps its not the card having problems, but the version of ndiswrapper not working with ubuntu very well.

---

### Post by _Mo on 2006-03-31
I have the same problem. I'm using a "Siemens Gigaset USB Adapter 54" with ndiswrapper-1.11 and randomly i lose my connection. If I reboot my system, a error related to ndiswrapper appears. I have to shut down my PC completly to use ndiswrapper again.

EDIT: Sorry for my Englisch, I'm German...

---

### Post by Zaxor the other @ss isn't on 2007-02-01
> **_Mo said:**
> I have the same problem. I'm using a "Siemens Gigaset USB Adapter 54" with ndiswrapper-1.11 and randomly i lose my connection. If I reboot my system, a error related to ndiswrapper appears. I have to shut down my PC completly to use ndiswrapper again.

EDIT: Sorry for my Englisch, I'm German...

I can't even get my Siemens Gigaset USB Adapter 54 to work...how did you do it

---

