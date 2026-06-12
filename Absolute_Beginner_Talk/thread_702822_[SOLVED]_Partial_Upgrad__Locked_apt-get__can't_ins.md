---
title: "[SOLVED] Partial Upgrad / Locked apt-get / can't install updates"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by crjackson on 2008-02-20
Okay, so I've been messing around for several days now trying to get updates to work again.

A few days ago there were some updates showing on the notifier.  I told it to get the updates, and it told me there was a partial distro upgrade.  I told it to install the partial upgrade, and several hours later it was still hung at fetching (the 1st step).  I couldn't get the process to stop, so I did a forced close.

Now, I can't get any updates.  It still shows a partial upgrade, but also a locked process with synaptic or something.

I've looked through the old threads with similar problems and I found no solutions.  I know it's probably simple, but so far I've had no luck.

Thanks...

---

### Post by neurostu on 2008-02-20
have you tried reseting your machine?  When you stop a synaptic you must KILL it before you can rerun it. 

I would recommend reseting the machine and then re run the update.

---

### Post by spiderbatdad on 2008-02-20
Obviously you've tried sudo dpkg --configure -a
I think partial upgrade are due to resources being unavailable at the server.

---

### Post by crjackson on 2008-02-20
> **neurostu said:**
> have you tried reseting your machine?  When you stop a synaptic you must KILL it before you can rerun it. 

I would recommend reseting the machine and then re run the update.

Yes, I've tried that.  No dice...

---

### Post by crjackson on 2008-02-20
> **spiderbatdad said:**
> Obviously you've tried sudo dpkg --configure -a
I think partial upgrade are due to resources being unavailable at the server.

Well... it's not the partial upgrade I'm concerned about so much.  It's the fact that it won't let me get regular updates either.  I have 10 machine running and they are all updating properly except this one.  Updates come through for the other machines, but this one won't let me update at all.

---

### Post by spiderbatdad on 2008-02-20
maybe sources.list has some bogus entries like automatix?

---

### Post by crjackson on 2008-02-20
> **spiderbatdad said:**
> maybe sources.list has some bogus entries like automatix?

I've never added anything to the default repositories available to ubuntu except medibuntu.  Automatix never touches my systems.

---

