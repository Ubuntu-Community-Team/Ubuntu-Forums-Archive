---
title: "Downgrading (edgy to dapper)"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by tsr on 2007-02-26
Hi,

Ok, so I have this comp wich is a bit unstable using edgy (mostly wifi issues that aren't solved). The comp is used by a "not so into this computer thing" friend of mine so  we have been thinking about downgrading to dapper since it's a LTS of ubuntu.

1. is this even the thing to do? (what we want to accomplish is wifi and general stability)
2. I'm thinking about just backing up the home dir and then repartition the drive and install /home on a separate partition, how would this affect personal software settings (eg .whatever in the homedir)? Should all those be deleted, or should we first give it a try?

Any help appriciated!

(We have been struggling with this comp for 3 months, and it's quite difficult since wifi isn't working and he hasn't got wired internet connection at home, the comp at hand is a HP dv2030 (or something similar))

/tsr

---

### Post by chuckyp on 2007-02-26
Definately back up your /home then all your settings would be migrated.  Putting /home on its own partition is the way to go IMO.  That way you can whipe / and just reinstall whatever variant of nix and have all your settings and files still there.

---

### Post by jamesstansell on 2007-02-26
1. LTS just means the worst bugs will continue to be addressed for 5 years instead of 18 months.  Most wifi problems wouldn't be fixed unless there was a security issue.  In general wireless in edgy is better than dapper so unless your specific card is known to be better in dapper then I wouldn't suggest it.

2. Yes, /home on its own partition is a good thing.  I guess your question is about keeping personal setting when downgrading.  The safest course would be to just completely clear them out to start with.  I say that because even though most applications might be fine any that make a big jump (like the Firefox 1.5 to  2.0) could easily have new properties or even formats that the older version isn't prepared to handle.

I've heard good things about the new feisty prereleases.  I almost wonder if that might be a better direction to go.  You might consider trying out the live CD to see if it does better with your wifi networking.

In general, unless dapper was working for you before, I wouldn't suggest going to it.  Resolving the edgy issues will probably work better.

Perhaps there is a LoCo team or Linux Users' Group in your area?  Getting local help might make a difference for you.

Regards,

-james.

---

