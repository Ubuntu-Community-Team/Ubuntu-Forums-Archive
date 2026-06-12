---
title: "Where's the best way to find packages?"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by pdxuser on 2007-03-18
For Windows users, Download.com is the best resource for finding new software, with its ratings and reviews being especially helpful in finding out which program is best for what you want to do.  But with Ubuntu, is there a site that's better than a PM like Add/Remove or Synaptic?  Because even with Add/Remove, which has a popularity rating system, a package like Totem Movie Player is rated better than mplayer, when almost every comparative review I find online favors mplayer (as do I, given that mplayer played Real/Win files out-of-the-box and I've yet to get Totem to do the same).

---

### Post by Lord Illidan on 2007-03-18
> **pdxuser said:**
> For Windows users, Download.com is the best resource for finding new software, with its ratings and reviews being especially helpful in finding out which program is best for what you want to do.  But with Ubuntu, is there a site that's better than a PM like Add/Remove or Synaptic?  Because even with Add/Remove, which has a popularity rating system, a package like Totem Movie Player is rated better than mplayer, when almost every comparative review I find online favors mplayer (as do I, given that mplayer played Real/Win files out-of-the-box and I've yet to get Totem to do the same).

Hmm...not much in the way of sites that I know of..
The real thing is to experiment, hehe...and ask on forums and websites what they think of such software.

Regarding totem, aye, I use VLC, Xine and mplayer instead. I don't know how totem is rated higher or indeed, why it is default.

---

### Post by pdxuser on 2007-03-18
Aha, I use Xubuntu, so I didn't know Totem was in the Ubuntu release.  That's why it's rated as more popular, because practically every Ubuntu user has it by default, and that's how popularity is defined.  You can opt-in to have your computer report all that's installed for use in the popularity rankings.  But obviously, most-used doesn't mean best.

BTW, what do VLC and Xine do that mplayer doesn't?  mplayer doesn't seem to do Winamp playlists out-of-the-box, so I can't take advantage of shoutcast.com yet.

---

### Post by soc on 2007-03-18
> **Lord Illidan said:**
> Regarding totem, aye, I use VLC, Xine and mplayer instead. I don't know how totem is rated higher or indeed, why it is default.

The stars show the popularity, not how good the programs are!
Therefor totem gets a good rating, because it is preinstalled on all ubuntu-systems.

Just ask in the forums.
Is there anything particular which you are looking for?

---

### Post by jvc26 on 2007-03-18
Asking on the forums can be a good way to find out what people like and why, albeit it can become hijacked by flamers if its a particularly controversial topic. Testing things out yourself is also useful and finding persoanl preferences - I have used Rhythmbox, Amarok, Listen and Songbird now over time changing due to particular preferences at the time. Having the freedom of such variety means that its easy to switch if one has something you particularly desire which the other one doesnt.
Il

---

### Post by Lord Illidan on 2007-03-18
> **Illuvator said:**
> Asking on the forums can be a good way to find out what people like and why, albeit it can become hijacked by flamers if its a particularly controversial topic. Testing things out yourself is also useful and finding persoanl preferences - I have used Rhythmbox, Amarok, Listen and Songbird now over time changing due to particular preferences at the time. Having the freedom of such variety means that its easy to switch if one has something you particularly desire which the other one doesnt.
Il

About the flamers part...well, I don't think we've had too many flamer hijacks over programs...

And, yes...as I said before, don't be afraid to experiment. Download and try as many apps as you wish.

---

### Post by pdxuser on 2007-03-18
If I install and then remove a bunch of packages with a package manager, can I trust that my machine would be exactly like it is before I install, or would I likely have built-up residue of abandoned apps residing somewhere?

---

### Post by Lord Illidan on 2007-03-18
> **pdxuser said:**
> If I install and then remove a bunch of packages with a package manager, can I trust that my machine would be exactly like it is before I install, or would I likely have built-up residue of abandoned apps residing somewhere?

I can't respond with an exact answer to that question. However, in synaptic, for example and apt-get there is the option to purge an application, which completely deletes the application, even it's configuration files.

---

### Post by pdxuser on 2007-03-18
> **Lord Illidan said:**
> There is the option to purge an application, which completely deletes the application, even it's configuration files.
The config files aren't normally removed?  And what about dependencies?  Don't package managers track dependencies and remove ones that are exclusive to any package you decide to remove?

---

### Post by Lord Illidan on 2007-03-18
> **pdxuser said:**
> The config files aren't normally removed?  And what about dependencies?  Don't package managers track dependencies and remove ones that are exclusive to any package you decide to remove?

AFAIK, configs and dependencies aren't *automatically *removed. But apt-get will detect dependencies that you have no need for and will tell you how to uninstall them.

---

### Post by jvc26 on 2007-03-18
Usually it tells you when you next install/remove something that here is a list of packages which are no longer required, and you can type:
```

sudo apt-get --purge autoremove

```
to remove them on the whole.
Il

---

### Post by mcduck on 2007-03-18
> **pdxuser said:**
> 
BTW, what do VLC and Xine do that mplayer doesn't?  mplayer doesn't seem to do Winamp playlists out-of-the-box, so I can't take advantage of shoutcast.com yet.

Xine has absolutely fantastic picture quality & video/deinterlacing filters which make it superior for movie use, while VLC plays pretty much any media file you throw at it..

I use Totem for small random movie clips, mplayer mainly as browser plugin, Xine for movies and VLC when everything else fails.

---

### Post by Lord Illidan on 2007-03-18
> **mcduck said:**
> Xine has absolutely fantastic picture quality & video/deinterlacing filters which make it superior for movie use, while VLC plays pretty much any media file you throw at it..

I use Totem for small random movie clips, mplayer mainly as browser plugin, Xine for movies and VLC when everything else fails.

Not to mention that vlc can stream movies across a network and that both of them can play dvds with menus!

---

