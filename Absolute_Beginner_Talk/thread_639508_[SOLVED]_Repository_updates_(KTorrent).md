---
title: "[SOLVED] Repository updates? (KTorrent)"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-12-13
How often are the repositories updated?
Is there a place to see a timeline for updates or see who is working on updates for a particular app inside a Repository ?

The reason I ask is because I need to update KTorrent to the latest version [2.2.4](http://ktorrent.org/index.php?page=downloads), but the "Synaptic Package Manager" is claiming 2.2.1 is the latest version:

[img]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/PackageManager-ktorrent.png[/img]

Any way to find out when this will be updated to reflect the latest version ([2.2.4](http://ktorrent.org/index.php?page=downloads)) ?

---

### Post by mp4215 on 2007-12-13
It depends. Sometimes they are updated right away (for security fixes among other things) and sometimes it takes a while (waiting for a package to be declared "stable" or maybe the package manager(s) don't have time to update it).

Maybe someone else will come along and have a more concrete answer.

---

### Post by BassKozz on 2007-12-13
I guess my question is, is there a way to watch what the "package manager(s)" are upto, i.e. somesort of timeline or roadmap for updates? or way to notify the "package manager(s)" of updates?

You see the upgrade from KTorrent 2.2.1->2.2.3->2.2.4 fixes a flaw in the webGUI, where the webGUI's cookies were getting screwed up and you would need to login every time to clicked a link or tried to refresh a page (kinda a pain in the rear).  So I would love to have this fixed but it's not currently available in the 'synaptic package manager'.  So I could always compile myself (after [getting some help](http://ktorrent.org/forum/viewtopic.php?t=2135)), but if I compile it myself will I still be able to use the 'synaptic package manager' to uninstall, upgrade, etc... in the future, or when one compiles his/her self they are on their own and no longer can use the 'synaptic package manager' ??? 

This is confusing to me:confused:

---

### Post by mp4215 on 2007-12-13
I dont think that there is a road map of any sorts. I would think that the package managers are aware in some timely fashion that the packages are updated. I am not sure why they would or would not update a package.

If you compile it on your own you are still abel to use synaptic. The one flaw is that if you want to completely remove the package you would have to do it manually, not through synaptic. But if a future version comes out and is released in the repositories you are still able to upgrade it even if you compiled a previous version.

Hopefully that was clear ;).

---

### Post by FuturePilot on 2007-12-13
It won't get updated until Hardy. The repos get frozen at release. The only way it would get updated is if it got backported.

---

### Post by BassKozz on 2007-12-13
> **FuturePilot said:**
> It won't get updated until Hardy. The repos get frozen at release. The only way it would get updated is if it got backported.
Really...
Thats a bummer :(
Well, when does Hardy come out?

looks like I might have to compile myself... scary thought for a newb like me ;)

---

### Post by mp4215 on 2007-12-13
> **B/-\ssKozz said:**
> Really...
Thats a bummer :(
Well, when does Hardy come out?

looks like I might have to compile myself... scary thought for a newb like me ;)

Hardy comes out in early 4/08 I believe. 

Don't worry, compiling is not brain surgery, and if you run into problems the people here can help :).

---

### Post by maybeway36 on 2007-12-13
Try adding the backports to your repo list.

---

### Post by stchman on 2007-12-13
You can get Ktorrent 2.2.2 from [www.getdeb.net](www.getdeb.net)

I found that is offered a big improvment over the 2.2.1 that the repos offer.

---

### Post by BassKozz on 2007-12-13
> **FuturePilot said:**
> It won't get updated until Hardy. The repos get frozen at release. The only way it would get updated is if it got backported.
> **maybeway36 said:**
> Try adding the backports to your repo list.
Thanks Guys... I added backports to the repo list, and 2.2.4 showed up and I installed. :D

How safe is it to keep Backports enabled on my repos list and install backports? Just as safe as other upgrades?

---

### Post by FuturePilot on 2007-12-14
> **B/-\ssKozz said:**
> Thanks Guys... I added backports to the repo list, and 2.2.4 showed up and I installed. :D

How safe is it to keep Backports enabled on my repos list and install backports? Just as safe as other upgrades?

You should be fine. I always enable the backports and I've never had any huge problems. And if you do run into an issue you can always force an older version.

---

### Post by louieb on 2007-12-14
> **FuturePilot said:**
> You should be fine. I always enable the backports and I've never had any huge problems.
Ditto...  Same here.

---

### Post by BassKozz on 2007-12-14
Great I'll keep Backports enabled... Thanks for all the help everyone :D

---

