---
title: "Need help replacing Totem plugin with MPlayer in Firefox"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ammark on 2007-04-20
**Problem Solved... ignore thread**

> I installed Feisty yesterday, and previously I was using Dapper.... Right now I want to set up mplayer as my default player/plugin in Firefox. I've already made Mplayer my default for playing my video files... but it seems that in Firefox its still set to totem (Movie Player).

I did a mozilla-mplayer plugin install and this is what it says now when I repeat it 

```
:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
``` 

But it is still using totem. I went to Firefox's Edit>Preferences>Content>File Types, and except for "SPL" (shockwave flash) there's no other format listed.

I also tried removing all the libtotem plugin files from /usr/lib/firefox/plugins temporarily to see if Firefox switches to Mplayer... which it didnt initially, but does now! :-D

How do I now go about to configure MPlayer to play embedded media in Firefox? 

---

### Post by riseringseeker on 2007-04-21
Would you care to share HOW you did this for the benefit of others like myself?

---

### Post by Pobega on 2007-04-21
Just remove mozilla-totem, or whatever the package is.

```
aptitude search "~i" | grep totem
```

---

### Post by AndyCooll on 2007-04-21
Ubuntu might not like you trying to delete the mozilla plugin, so try this:
```
sudo -s (to change to root)
cd /usr/lib/mozilla-firefox/plugins
mkdir oldtotemfiles
mv libtotem* oldtotemfiles
apt-get install mozilla-mplayer
```

:cool:

---

