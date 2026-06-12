---
title: "Losing files when upgrading?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Contradictions on 2007-12-09
Hi, I'm on Dapper, and before that I was on Breezy, and want to know how if it's possible to upgrade to Feisty (from CD) without losing my files and programs - this machine will not be connected to the net very often in the next few months - in the previous upgrade a friend did everything, but all my files and programs were lost, which you can imagine was very annoying :)

I'm sorry for posting this question again, but all the other threads I found referred to different distributions or used terminology I don't understand.

---

### Post by Contradictions on 2007-12-09
I'm not trying to be rude or facetious here - I seriously couldn't understand half the replies - this is the absolute beginner section after all - and every thread I read didn't make it clear whether this applied to the upgrade I plan.:confused:

---

### Post by red_Marvin on 2007-12-09
You should be able to upgrade without problems, but it's *always* good to backup important data before big changes. -But you seem to be aware of this already. ;) (Me too)

This *should* (if I remember correctly, but double check with whatever threads you've found while searching on your own)
upgrade your system without you losing any data, me I prefer clean reinstalls, but that's me:

press alt+f2
type *gksudo gedit /etc/apt/sources.list* and press enter
the opened file should contain some text where you should change *dapper* to *edgy*
then open a terminal and type *sudo apt-get update* (enter) and when it returns *sudo apt-get dist-upgrade*



Finally, you can't normally expect an answer in half an hour, the forum is popular, but not that popular. ;)

---

### Post by Contradictions on 2007-12-10
Thanks, I'd heard different things, and it was nice to get some confirmation. This site is greatly appreciated!

---

