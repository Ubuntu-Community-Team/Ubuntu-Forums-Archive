---
title: "Unable to update after installing 8.10 on G4 iBook"
date: 2009-01-30
forum: Apple Hardware Users
---

### Post by barti on 2009-01-30
I've installed 8.10 on my G4 iBook, and after following the various FAQs I've now got it booting, with most things working. The network is present and I can browse the web, however I'm unable to update.

Running apt-get update results in a lot of messages similar to the following:

```
Err http://ports.ubuntu.com intrepid-updates/main Translation-en_GB
Unable to connect to ports.ubuntu.com http:
```

I've tried at several different times over the past few days, and haven't had any success. Is there a known problem with ports.ubuntu.com (or more specifically, the PPC related archives)?

Steve

---

### Post by blazemore on 2009-01-30
Can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by cyberdork33 on 2009-01-30
> **barti said:**
> I've tried at several different times over the past few days, and haven't had any success. Is there a known problem with ports.ubuntu.com (or more specifically, the PPC related archives)?
I just opened 
[http://ports.ubuntu.com](http://ports.ubuntu.com) in my browser and it worked fine... so not a server issue. Try again now, and if you still have issues, it may be related to your internet connection...

---

### Post by mkvnmtr on 2009-01-30
I have at times had that error. Many times it involves some english package. It resolves itself in a little time. I think it is just a problem with the server. As ppc users we can't just change mirrors to go to another repository. I have noticed yesterday the download speeds were much slower than normal on the three systems that I ran updates for. I would think that the servers may be loaded down. If I was you I would just wait a while before trying to do anything.

---

### Post by barti on 2009-01-30
I think it was a combination of two things - the server being a little unresponsive, but mainly the iBook getting rather hot, and causing the ethernet to drop out intermittently.

Having left the machine to cool for a while, and using the WLAN instead of the Ethernet connection it's now downloading the updates successfully.

Stephen

---

### Post by mkvnmtr on 2009-01-30
Getting hot is a big problem. In the last couple of weeks I have had a problem with heat on my Ibook. I have had it 5 or 6 years and have never heard the fan. It came on one time very strongly in Ubuntu bbut now I never hear it. I was getting to the point that it would become unresponsive. I have now set it up off the desk about an inch and have an external fan blowing on it all the time. I am having no more problems heating up and the case never feels hot. The only downside is sometimes my hands get cold. Remember these are old machines.

---

### Post by cyberdork33 on 2009-01-30
This guy had the same problem:
[http://ubuntuforums.org/showthread.php?t=1054955](http://ubuntuforums.org/showthread.php?t=1054955)

I will redirect him here. Sounds like there may have been some server issues.

---

### Post by barti on 2009-01-30
> **mkvnmtr said:**
> Remember these are old machines.

Indeed they are, - the reason for installing Ubuntu on them is to give them a little bit more life! They're for a local school and are destined to be used as wireless Internet access research machines (amazingly, the batteries seem to be fairly healthy after all this time!). If the students are happy with Ubuntu, I think the school may go for a bunch of Linux-based Netbooks too :)

Stephen

---

