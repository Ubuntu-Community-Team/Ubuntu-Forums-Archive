---
title: "WiFi Card Compaq Presario v5000"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by rechelon on 2007-05-08
Jeeze this is embarrassing...

I swapped over my laptop to Dapper Drake from XP a few months ago and got everything working, with the exception of the WiFi card.  I tralled around looking for a good guide for setting up the drivers, etc, but found a bunch of conflicting and generally confusing stuff.  Everything seems to be oriented towards setting up a network or other far more complicated undertaking.  Everyone seems to have their own completely different "totally simple" method, few of them seem applicable and those I've tried have ended in aggravatingly non-committal ways.  Of course, being a busy student this wasn't really a problem.  But the time has come to leave the batcave and venture out into the world. 

 I need to be able to walk into a cafe and leech WiFi without hassle.  So far I'm not even sure if my laptop can read the card.  I assume it can't, but I'm so ignorant it might be I just need to change some setting.

Apparently I know absolutely nothing about WiFi anything or installing drivers on Ubuntu.  So I'm a little ol' grandma.  Please walk me through it?

I'm running Dapper (and pretty much nothing that wasn't packaged with it) on a Compaq Presario v5000.

I'm really sorry for wasting your time on something this simple.  For what it's worth, out of embarrassment I've waited four months to post such an obviously RTFM post.

---

### Post by eltorodeoro on 2007-05-08
find out what type of card you have:
```
lspci
```
should be near the bottom.
i'm not sure what compaqs use, but broadcom is a popular chipset, and equally as troublesome.  find your chipset and use a keyword search in these forums to find a howto.  there are plenty out there, even for something as tricky as broadcom wireless.

stick with it and read, read, read.  don't be afraid to ask questions, and don't worry about the flames...  they burn out eventually.  those folks seem to forget they were once nubees too.

---

