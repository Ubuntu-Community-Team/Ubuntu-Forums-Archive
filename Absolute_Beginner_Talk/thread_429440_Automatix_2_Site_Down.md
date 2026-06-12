---
title: "Automatix 2 Site Down?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by popeyeray on 2007-05-01
I was able to completely get my laptop updated through Automatix2 on Fiesty, now a day later I am trying to update my Desktop and it appears all links to it just say 
"Connecting to www.getautomatix.com..." and then nothing. I've searched these forums, and googled for an announcement but have found nothing. Can someone tell me if this is a regular occurrence, if so does the site usually come back up in a short time?

---

### Post by Seisen on 2007-05-01
I personally don't recommend using Automatix because people have ended up having many problems upgrading their distribution.

---

### Post by taurus on 2007-05-01
You need to either wait for the site to get back up again or comment out the repos in /etc/apt/sources.list related to Automatix.  

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by jrusso2 on 2007-05-01
I have not had any issues with Automatix on Edgy or Feisty

---

### Post by starcraft.man on 2007-05-01
I don't use automatix either, while its nice to point new people to that to get things started. You should learn the manual way to install via the repos and terminal.

In the interim that automatix is down, use [UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") as your helper :) Also look at the Edgy guide for some programs not listed in feisty.

---

### Post by Michaelt74 on 2007-05-01
What are you trying to install using Automatix?

---

### Post by gn2 on 2007-05-01
> **popeyeray said:**
>  I've searched these forums, and googled for an announcement but have found nothing. Can someone tell me if this is a regular occurrence, if so does the site usually come back up in a short time?
.
Announcement and info here:
.
[http://ubuntuforums.org/showthread.php?t=429209](http://ubuntuforums.org/showthread.php?t=429209)
.
Hopefully it'll be sorted soon.

---

### Post by PriceChild on 2007-05-01
You may want to read [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13) also.

---

### Post by starcraft.man on 2007-05-01
Thats a shame that some moron DDOSed automatix, people like that really need to find better uses of their time... like coding open source :)

---

### Post by neufelry on 2007-05-01
tis a shame, i really wanted to try it this morning

---

### Post by Drakkor on 2007-05-01
> I personally don't recommend using Automatix because people have ended up having many problems upgrading their distribution.
I've heard of many people having problems updating their distribution anyways ! Which is why I always just clean install mine, and i never had a problem with Automatix. Dapper>Edgey>Fiesty  :)

---

### Post by useResa on 2007-05-01
AFAIK the site is back up again.
My *sudo apt-get update* did not produce any errors anymore and both [the site]("http://www.getautomatix.com/") and [the forums]("http://www.getautomatix.com/forum/index.php") can be reached again.

---

### Post by popeyeray on 2007-05-01
Okay, I usually do all the optional updates through apt, or synaptic but it was late and I just wanted to try the latest Automatix. I have since found that the site is back up but thank you all for you comments and assistance.

---

