---
title: "Two dual boot PCs to network"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-07-14
We have two PCs, both dual boot Ubuntu Feisty and Win XP Pro.

They both connect to a router (one via homeplug, the other directly) and can both access the web, so clearly the hardware is correct!

However, I am a bit unsure where to start! I looked at this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

and have installed Samba, which is what I think I need to do.

Thereafter, I get a little lost! What are my next best steps - get them connected both in Win or both in Ubuntu first, or can I plunge straight into connecting this one (mainly Ubuntu) with the other one (mainly Win)?

Please feel free to use very simplistic terms in your reponses!!!!

Thanks

---

### Post by ugm6hr on 2007-07-14
In Windows - it's just a case of running the *setup home network wizard* on each computer (appears on left pane if you go to *My Network Places*.  Then just right-click on any folders you want to share, and activate sharing.

For Ubuntu - I saw that link you gave, and was a bit perplexed as well.  I got my dual OS network working with minimal effort.  There are still some problems, but it might offer you a place to start:
[http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734)
Just remember to use *nautilus* instead of *thunar* (for Ubuntu instead of Xubuntu).

Hope it helps.  And if you find an easier solution, point me towards it.

---

### Post by qprfact on 2007-07-15
Yep, that worked thanks! Now am able to access either OS from either PC! Just what I wanted, so thanks a lot.

Not sure about this pyNeighborhood sudo thing, though as with you I won't be running it that often (and presumably once the drives are mounted the teminal window can be closed and you're no longer running anything as su?)

---

### Post by ugm6hr on 2007-07-15
Glad it helped.  I think the Ubuntu wiki is far too complicated for people looking to get a Windows-like home network running with a few clicks.

As for running pyNeighborhood as su - it's more inconvenient than anything else.  And as a perfectionist - I need to find an answer!

---

