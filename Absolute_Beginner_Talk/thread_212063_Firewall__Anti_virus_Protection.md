---
title: "Firewall / Anti virus Protection?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2006-07-09
Hi again all

 I have done a search on this forum regarding anti virus and firewall/ spyware software, and most people say:

 Anti virus = not needed
 Firewall = not sure on this one
 Spyware = not needed

It just feels so weird after years of using windows and having to install ALL of the above programs, to then go on the internet without anything to protect me !

---

### Post by DR_K13 on 2006-07-09
I always run  A firewall

as far as Anti-virus and anti-spyware goes - none is needed/

---

### Post by cyberlite on 2006-07-09
Ubuntu has a build in firewall.

---

### Post by FPStanley on 2006-07-09
Ah yes, the joys of Linux...

Anyway, if you are concerned about spreading viruses to your Windows friends via email and the like, you could look into ClamAV.

Spyware is not an issue, however, if you can't stand website advertisements, check out Adblock & the Adblock updater on the Mozilla Foundations site.

As for using a Firewall, do you have a router?

---

### Post by moffa on 2006-07-09
Although ubuntu has a built in firewall if you need to configure it you should install Firestarter. In a terminal you just type
```
 sudo apt-get install firestarter 
```

---

### Post by Dinerty on 2006-07-09
People say Firestarter is a good firewall?

I do have a router which has a firewall built into it

---

### Post by MrHorus on 2006-07-09
> **Dinerty said:**
> 
Spyware = not needed


Spyware is never needed heh :)

As far as an antivirus goes then there are very, very few Linux viruses out there that personally, I wouldn't waste the CPU cycles but if it makes you feel better then go ahead and use one and as far as a firewall goes, you can configurean Intrusion Detection System (IDS) and iptables whatever way you want or you can install some sort of script or application to do this for you but I would certainally want SOMETHING in place to stop anyone accessing your box willy-nilly.

---

### Post by Dinerty on 2006-07-09
> **moffa said:**
> Although ubuntu has a built in firewall if you need to configure it you should install Firestarter. In a terminal you just type
```
 sudo apt-get install firestarter 
```

Thanks for this i will give it ago once I'm all sorted.


Thanks for all your help guys

---

### Post by FPStanley on 2006-07-09
> **Dinerty said:**
> People say Firestarter is a good firewall?

I do have a router which has a firewall built into it

Well, as long as you do not have DMZ enabled on your router, I personally, I would not worry about the firewall issue. However, like everyone else has stated more or less, if you are a little paranoid about security, tweaking the firewall provided with the base install of Ubuntu should be good enough.

---

### Post by xarx on 2006-07-09
> **cyberlite said:**
> Ubuntu has a build in firewall.
how is the firewall configured by default? i mean what type of services it blocks/allows...

as for anti virus, most are scanners right? or do they also clean virus? aegis could only scan, clamav i can't remeber...

thnks in advance! :)

---

### Post by hairmetal4ever on 2006-12-26
So there are no linux viruses or what?  Seems weird.

---

### Post by OldTimeTech on 2006-12-26
So far it seems that virus makers have it out for M$ and they leave Linux alone for the most part.

---

