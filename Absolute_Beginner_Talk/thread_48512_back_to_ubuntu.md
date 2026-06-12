---
title: "back to ubuntu"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by Snitz on 2005-07-12
I installed lindows, but I couldn't create a new pppoe connection
so I uninstalled it and tried to install winxp back but it wouldn't let me, it kept telling "no operating system"
so I installed winme, few times and tried to install winxp back but also didn't work.
so I installed my redhat 9.0 back, hoping to get the pppoe work, but I didn't know what was it's command in the terminal
so I installed ubuntu back on my machine, I had to make my HDD 1 partition, and now im using it, but it could freeze any minute now!
this was the reason why I got it off
this proccess took 4 hours :(

now im back to ubuntu, the good thing is that it's not freezing anymore, but I have few issues (nothing impossible)

first: my sound isn't that clear, ubuntu has detected my sound card, but the sound isn't very clear, it's the same on redhat, is there anyfix?
second: when I installed ubuntu, I have to delete all my partitions and make them as 1 partition (40GB)
is there a way to resize it and repartition it into 2 without formatting again or fdisk?

---

### Post by Snitz on 2005-07-12
my pc is still freezing out, but now I know the reason 
it's from the update manager
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
when I did they said and ran the commands, my pc started to freeze when I restored it as it was, it's not freezing anymore.
why is it doing that?

---

### Post by trash on 2005-07-13
Are you doing an upgrade with the extra repositories enabled?

I once asked if it is ok to do this and the answer was no,  it could break something.

---

### Post by bored2k on 2005-07-13
[QUOTE=Snitz]my pc is still freezing out, but now I know the reason 
it's from the update manager
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
when I did they said and ran the commands, my pc started to freeze when I restored it as it was, it's not freezing anymore.
why is it doing that?[/QUOTE]
 Maybe the cron job that updates the Update manager is acting bananas on you ? What if you remove the update manager (NOT synaptic) ?

---

