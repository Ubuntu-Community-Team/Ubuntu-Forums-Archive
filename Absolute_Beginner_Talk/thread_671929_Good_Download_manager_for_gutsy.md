---
title: "Good Download manager for gutsy?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by abicash on 2008-01-19
I have searched a lot and dint find what I wanted.Here's what I need..
I am in India with BSNL broadband (night unlimited download)
I have setup the BIOS of my PC to wakeup at 2.15am every night.I just want to schedule all downloads to be undertaken till 7.30am in the morning (my happy hours 2am-8am) At 7.30 my PC should be shut down/suspended whatever is easy.I should also be able to schedule and download torrent files with this manager.
I searched a lot and learned about crontab and scheduler in ubuntu but only half the work is done here (shutting down pc) ,how to wake it up?(if I do nothing to BIOS to wake up)
I cannot get a bridged connection on my ubuntu system (tried rp-pppoe and pon dsl-provider but doesnt work) So I have an always on connection.So I will have to keep my connection 'on' all the time.

So any geek-gods with a script/package that does all the things above?

p.s. Posted here since I dint know where to post.

---

### Post by intel on 2008-01-19
pppoe dialer should work under linux, you may have to fiddle with it for the correct settings.(searc for setting up your particular modem)

for timed torrent downloads, you have to use the featureful Azureus client
(search for a plugin that schedules bandwidth, in night unlimited, remove bandwidth limits, otherwise restrict bandwidth to zero) azurus is running the whole time, just not downloading otherwise

for normal http/ftp downloads scheduling, use crontab & wget,
wget is the most feature complete download manager, but its command like, which is good, it takes less resources.

---

### Post by abicash on 2008-01-19
Hi intel thanks for the reply

I am lookin at the topics you stated and for the time being I have got IDM running through wine.

But is there a scipt or something to wakeup PC?

---

