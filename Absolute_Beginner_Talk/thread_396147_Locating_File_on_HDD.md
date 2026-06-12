---
title: "Locating File on HDD"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by captin_moor on 2007-03-29
Hi there guys and girls, I have a bit of a problem. I am relatively new to Ubuntu and am just really starting to get into the fun of networking several machines and doing all sorts of fun things with them. However I may have inadvertaintly caused a bit of a problem. I had a round 5 gigs of files stored on a link drive using NFS, now I am unsure exactly which PC was the host and which was the client as I got a bit confused when I was following the HOWTO: Needless to say I believe that I have located them setting on server sxubu1, the only reason that I know this is that its HDD is saying that it is at 85% which is about right. But I all these files no longer exist in the linked drive that I created. So where oh where could they have gone. 

I have tried several find commands on the files extentions and names that where located in the drive but still have had no luck. 

So My Question is: Is there anyway of seeing where these files are actually located and why if they are no longer in the dir that I put them in, are they taking up HDD space. 

Sorry if this is a real newbie question but have tried searching the web for days and this is my last resort apart from a format. 

Look forward to hearing from you soon. Cheers

---

### Post by PointSource on 2007-03-29
If you accidentally or deliberately deleted them, then they may have been moved to "/home/YOUR_USERNAME/.local/share/Trash/files".

---

### Post by captin_moor on 2007-03-29
> **PointSource said:**
> If you accidentally or deliberately deleted them, then they may have been moved to "/home/YOUR_USERNAME/.local/share/Trash/files".

Thanks mate, but for starters that dir does not exist. And secondly I dont actually think that I deleted them. They where sitting in a mounted drive and now they are gone. Yet the space is still being takin up on my HDD though. Thanks for the imput mate. Much appreciated.

---

