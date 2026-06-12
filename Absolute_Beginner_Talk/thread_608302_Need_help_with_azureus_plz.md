---
title: "Need help with azureus plz"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by bluet0oth on 2007-11-09
i just finished installing ubuntu 7.1 with base updates
and tried installing azureus with sudo apt-get install azurues
when i run it is shows the splash screen and blinks with the initial setup screen before closing
i'm running java1.5

ne tips?? also is azureus vuze running on linux yet?

---

### Post by K.Mandla on 2007-11-10
Moved to Absolute Beginner Talk.

---

### Post by WinterWeaver on 2007-11-10
aye... I used to use the latest Azureus... but I switched to Deluge

give it a go... it's great :) , and it's in the repos.

If you want to stick with Azureus, you will also need Sun Java installed to run it nicely.
you can also do this from Add/Remove.

---

### Post by jingo811 on 2007-11-10
Don't think so Vuze is still beta even in Windows right?

Remove what you installed and use the Add/Remove or Synaptic to install Azureus instead that's how I did.  But shouldn't make any difference compared to apt-get but that's what I used.

```
$ sudo apt-get remove azureus
```
Applications> Add/Remove> Azureus


Deluge and Ktorrent are pretty good programs but much traffic is being filtered or something by default so you get like 30 peers with those compared to Azureus who punches a hole in your router in order to give you 100 something peers anytime.  Which isn't a good thing but not many ppl can or have the will to learn how to configure their routers so Azureus is the most peer efficient one of them.

---

### Post by empty89 on 2007-11-10
u will not wan to use Azureus it use up a whole bunch of memory and lag ur comp.
Try using ktorrent even though it is for kde, it works great on gnome. it is very similar to Azureus too.

---

### Post by WinterWeaver on 2007-11-10
I used Ktorrent a while back, and although it's good, it does not come close to azurues.

I used to use some features in Azurues which was unavailable in KTorrent.

.... lol.... I still vote Deluge ^_^

---

### Post by jingo811 on 2007-11-10
I always had to wait 30+ minutes before reaching a 50+ kB/sec constant downstream with both Ktorrent and Deluge.  So I switched back to Azureus which gives me 200+ kB/sec constant downstream after only 3 minutes.
Tested on the same links.

---

