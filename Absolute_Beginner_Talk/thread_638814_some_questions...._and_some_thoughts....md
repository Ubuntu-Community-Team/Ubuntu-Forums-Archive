---
title: "some questions.... and some thoughts..."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-12-12
how can i schedule a file system check next time i reboot?

when i use xchat firestarter suddenly closes by it's own...(i dont even touch it) why?

is there a programm/frontend which could show me which ports/protocols are enabled/disabled (and what programms are using it) like a report at a specific moment or(better) perhaps it could create somekind of log only for internet activities?

i think a good idea would be to merge firestarter's & guarddog features into one programm..what do you think?

---

### Post by CatKiller on 2007-12-12
> **someoneouthere said:**
> how can i schedule a file system check next time i reboot?

```
sudo touch /forcefsck
```

I don't know about the rest

---

### Post by thelatinist on 2007-12-12
> **someoneouthere said:**
> how can i schedule a file system check next time i reboot?

when i use xchat firestarter suddenly closes by it's own...(i dont even touch it) why?

is there a programm/frontend which could show me which ports/protocols are enabled/disabled (and what programms are using it) like a report at a specific moment or(better) perhaps it could create somekind of log only for internet activities?

i think a good idea would be to merge firestarter's & guarddog features into one programm..what do you think?

To force a filesystem check, do

```
sudo tune2fs -C 60
```

This will set the number of times your filesystem has been mounted since last check to 60, which is surely greater than the default check interval on your system.

Why bother having Firestarter open anyway?  It's not your firewall, it's just used to configure your firewall.

---

### Post by someoneouthere on 2007-12-12
> **thelatinist said:**
> To force a filesystem check, do

Why bother having Firestarter open anyway?  It's not your firewall, it's just used to configure your firewall.

well firestarter is very handy especialy when you want to "instant" configure some settings without getting to terminal and have to pass a whole proccess... also you don't have to look 
to many different programms and settings the same time(even for the simpliest task)...just one...

---

### Post by thelatinist on 2007-12-12
> **someoneouthere said:**
> well firestarter is very handy especialy when you want to "instant" configure some settings without getting to terminal and have to pass a whole proccess... also you don't have to look 
to many different programms and settings the same time(even for the simpliest task)...just one...

Yes, I agree. I used Firestarter to configure my firewall, too.  But once your firewall is configured properly (a matter of a couple of minutes) you don't ever have to think about it unless you install some new server software or something.  And how often do you have to do that?

It's a huge waste of resources to keep Firestarter running constantly just to have one-click access to your ip-tables configuration.  Just create a launcher on your panel if Applications > Internet > Firestarter is too time-consuming.

---

### Post by someoneouthere on 2007-12-12
ok i agree but there should be a programm that monitor internet traffic only and why not... give a log to the system.... so if you actually get a hit you'll know where it came from....

---

### Post by Flyingjester on 2007-12-12
well there's wireshark, it's a packet sniffer.

---

### Post by thelatinist on 2007-12-12
> **someoneouthere said:**
> ok i agree but there should be a programm that monitor internet traffic only and why not... give a log to the system.... so if you actually get a hit you'll know where it came from....

I'm still not sure what you're worried about.  If you're worried about what the software on your own computer is doing, then you might want to reconsider what software you install.  If you are worried about attacks from other computers, a properly configured firewall should be plenty to protect you.  If you get an attack on a port you've opened, whatever server software you have listening on that port should tell you and keep a log.  If someone pings a stealthed port and gets no response, they'll soon go away.  Forgive me, it seems like paranoia to me.

---

### Post by someoneouthere on 2007-12-12
yeah i does seems paranoia to me also... lol.. i am a newbie trying to make something clear.... 
i guess...

---

