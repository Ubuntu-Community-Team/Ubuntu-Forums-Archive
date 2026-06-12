---
title: "Dist-Upgrade Checklist"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-09-28
Hey all,
I read that the upgrade is coming on Oct. 1
As a noob it will be my first.
I have seen threads about apps breaking when you do an upgrade is this true?
My setup is pretty much out-of-the-box save a few little eye candies:

dual monitor system (thanks to the help supplied by Bodhi-Zazen)
gdesklets
vmware
xdesktopwaves
nvidia driver
3ddesk
assorted little junk

I have gotten all of the window-configurations/panels/etc. on my system just how I like them, will the dist-upgrade affect any of those things?

I'm pretty sure im gonna have to run the ./config on vmware but im not sure about the system settings... 

Do people usually wait a little while before upgrading the distribution or can I do it the first day?  Will the new Edgy (I think thats the new one) be relatively bug free on Oct. 1 or is there usually a period of time where the developers and community get the kinks ironed out?

Im really looking forward to doing my first dist-upgrade but thought I might try and figure out what to expect.

---

### Post by ThrobbingBrain66 on 2006-09-28
Edgy Beta is scheduled for release today.  The official release date for Edgy is Oct. 26th.

A clean install is a good way to go because it reduces the number of possible conflicts vs dist-upgrade.  that being said, if you dont have your /home on a seperate partition, you will lose all your settings by doing a clean install.

---

### Post by charles.g.moore on 2006-09-28
Luckily I did keep my /home on a separate partition, so does that mean that I can d-load and install fresh while leaving my home partition untouched?
Does'nt my home part. carry alot of hidden stuff that only works with dapper or are the things in /home going to be compatible with edgy?

Just so I understand correctly if I:
D-load the upgrade
Install into all my partitions (leaving the home part. untouched)
start up the new upgrade

I'll have all of my settings intact?

---

### Post by ThrobbingBrain66 on 2006-09-28
yes, since you have a seperate /home partition, youll be able to do a clean install and still be able to keep all of your settings in tact.  Of course, all the programs you added will have to be installed too.

---

### Post by Metacarpal on 2006-09-28
> **charles.g.moore said:**
> Luckily I did keep my /home on a separate partition, so does that mean that I can d-load and install fresh while leaving my home partition untouched?
Does'nt my home part. carry alot of hidden stuff that only works with dapper or are the things in /home going to be compatible with edgy?

Just so I understand correctly if I:
D-load the upgrade
Install into all my partitions (leaving the home part. untouched)
start up the new upgrade

I'll have all of my settings intact?

Yep - You'll just need to re-add your users.  Important: add the users in the same order you originally added them!  If you're not sure, go into System > Administration > Users and check each user's Advanced tab.  They're assigned numbers (like 1001)- you'll need to add them back in the same sequential order, or manually assign the same number when adding them.

---

