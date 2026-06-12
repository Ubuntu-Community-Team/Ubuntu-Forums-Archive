---
title: "Ack, Newer User needs help!!!!"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by SAMW on 2007-03-23
Hello,

I'm not a totally new ubuntu user, but this is a new install and i'm not a guru, so this seems like the right place to post. I recently did an over the net install of Edgy, after installing dapper from a cd. When i start my computer, i get a message from the update manager saying:

 "Error opening the Cache(E:Type '"deb' is not known on line 34 in source list /etc/apt/sources.list, E:The list of sources could not be read.)

That is it exactly, word for word. I think that the install messed up my sources list. This wouldn't really be a problem except for the fact that I now cannot open anything that that needs a "sudo type" prompt. My apt update and update manager are screwed, but my Synaptic is good......



Any suggestions?


Edit: AHHHH, silly me, i fixed it by sudo gedit /etc/apt/sources.list and changing the line. Sorry

---

### Post by milton1 on 2007-03-23
you could copy the sources list from the cd, then replace every 'dapper' with 'edgy'. However, you may still run into more glitches. Over-the-net upgrades are notoriously glitchy. For the fewest problems, a clean install is your best bet.

---

### Post by zvacet on 2007-03-23
You can put # sign in front of line 34 or you can create(copy/paste)new source list,this time for Edgy.This is just one of options
[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

