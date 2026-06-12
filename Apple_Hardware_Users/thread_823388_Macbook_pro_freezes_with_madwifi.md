---
title: "Macbook pro freezes with madwifi"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by rytmisk on 2008-06-09
Hi

I see that the apple intel forum has disappeared from the front page so I post here too. 

In post [http://ubuntuforums.org/showthread.php?t=671922](http://ubuntuforums.org/showthread.php?t=671922) there is a discussion about madwifi with Atheror ar5418 freezing and hanging after some unpredictable amount of time. This issue is apparently now fixed according to [http://madwifi.org/ticket/1017#comment:211](http://madwifi.org/ticket/1017#comment:211) but I am not able to understand how...

Anyone can help?

Ketil

---

### Post by mabovo on 2008-06-09
> **rytmisk said:**
> Hi

I see that the apple intel forum has disappeared from the front page so I post here too. 

In post [http://ubuntuforums.org/showthread.php?t=671922](http://ubuntuforums.org/showthread.php?t=671922) there is a discussion about madwifi with Atheror ar5418 freezing and hanging after some unpredictable amount of time. This issue is apparently now fixed according to [http://madwifi.org/ticket/1017#comment:211](http://madwifi.org/ticket/1017#comment:211) but I am not able to understand how...

Anyone can help?

Ketil

Mine freezes just when I unplug power cord and battery energy drops quickly deactivating AR5418.

It can be a battery issue or a power management problem or the worst case related with madwifi driver.  I am using the svn version 3545 because lattest versions doesn't work with kernel 2.6.24-19.

Ubuntu devs don't like MAc's ?

---

### Post by rytmisk on 2008-06-09
> **mabovo said:**
> Mine freezes just when I unplug power cord and battery energy drops quickly deactivating AR5418.

It can be a battery issue or a power management problem or the worst case related with madwifi driver.  I am using the svn version 3545 because lattest versions doesn't work with kernel 2.6.24-19.

Ubuntu devs don't like MAc's ?


Hm - must be something different from what I have been experiencing since my halts have been mostly with power plugged in. Using bittorrent however have been a certain way of making it freeze. Today I tested the latest svn again with a script I found through these forums - [http://ubuntuforums.org/showthread.php?t=798485&highlight=script+madwifi+svn](http://ubuntuforums.org/showthread.php?t=798485&highlight=script+madwifi+svn) and so far I've not had any dropouts despite having stressed the network load in different way. I do not mark this as solved until it has been working a few days though! (BTW this is with the 24-19 kernel)

Best regards
Ketil

---

### Post by cyberdork33 on 2008-06-09
I think the issue is related to network manager in conjuction with madwifi. This seems to work better if you use wicd.

---

