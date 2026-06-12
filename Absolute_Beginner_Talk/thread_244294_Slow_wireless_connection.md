---
title: "Slow wireless connection"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by epq on 2006-08-26
I am accessing the net through a wireless connection that requires a WEP key.
It is set up but it is running quite slowly.
Well, its seems to go at normal speed when it goes but it keeps halting.
Connecting through Windows works perfectly but I've recently installed Ubuntu and want to make the transition pernament.
Thanks

---

### Post by agrabah on 2006-08-26
Have you tried using knetworkmanager? It solved my troubles with wireless connections.
That is, if you're using kde; if you're using gnome try networkmanager; knetworkmanager is only a frontend for gnome's knetworkmanager.

And there is a good guide on ubuntu wiki:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28wireless%29)

Tine

p. s.: Please post more info for those who know more about networking than I do.

---

### Post by epq on 2006-08-26
I did a search for knetworkmanager on Add/Install but it told me it was not available on any software channel and that my system architecture may not support it

---

### Post by agrabah on 2006-08-29
What are you sporting? I use Intel Dapper, and had no problems installing it.

But I think I see yout problem... try running adept and search for knetworkmanager; it should be under available packages now.

Oh, just an afterthought - I noticed that the Add/Remove Programs utility tends to hide some packages; I don't know why. So I rather use adept now, or directly apt-get.

Tine

---

### Post by hkq35 on 2006-10-31
Is all the internet slow or just firefox?
I had the same problem, Firefox was painfully slow but Gaim and Evolution were quite fast.
 


If its just Firefox try Edit>Preferences> Connection settings (button)
select 'Auto-detect proxy settings for this network'

also check out [http://www.ubuntuforums.org/showthread.php?t=202838](http://www.ubuntuforums.org/showthread.php?t=202838)

---

### Post by fisherking on 2006-11-26
OOOh, thanks for the tip! Had trouble with my browsing but I thought I had a general "slow Internet connection problem". 

I changed the setting you recommended and now it works perfectly (so far!)
Thanks!

---

