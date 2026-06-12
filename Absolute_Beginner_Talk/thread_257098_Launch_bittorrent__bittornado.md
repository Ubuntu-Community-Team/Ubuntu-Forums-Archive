---
title: "Launch bittorrent / bittornado?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by smilinggoat on 2006-09-14
Hi, I just installed Ubuntu 6.06 to function as a home media center / torrent machine and so far so good.  I've run the Synaptic Package Manager and installed some extra packages, such as bittornado.  Now how do I run the darn thing?  When I try to "Run Application" and type "bittorrent" or "bittornado", nothing shows up.  Neither apps exist in /usr/bin .  I'm trying to start some new seeds, so just clicking on a .torrent file in Firefox will not do.

Any help on getting at least one of these running? Thanks!

---

### Post by halcyon on 2006-09-14
Ubuntu has a BitTorrent client installed by default, but I don't think it's capable of seeding torrents, you'll probably have to install another program like Azureus.

---

### Post by moore.bryan on 2006-09-14
[I]```
bittornado-gui
```
bittornado is far superior to the native bittorent piece; lots of added features.
[/I]

---

### Post by Marsolin on 2006-09-14
You may be using the command line versions. Try installing bittornado-gui or bittorrent-gui. The bittornado-gui package should add a menu entry so you can launch it that way.

---

### Post by smilinggoat on 2006-09-17
> **Marsolin said:**
> Try installing bittornado-gui or bittorrent-gui.

Is there an easy way to do this?  Synaptic Package Manager doesn't show that package.  Should I add a different server to the list of repositories?

---

### Post by moore.bryan on 2006-09-18
[I]try either
```
sudo apt-get install bittornado
```
or
```
sudo aptitude install bittornado
```
another alternative which i tried-out this weekend, but couldn't get to be as fast for me as bittornado was qbittorrent.
[/I]

---

### Post by Kurt` on 2006-09-18
If moore.bryan's commands result in a "package not found" or similar error, you may need to [enable the extra software repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories).

---

### Post by moore.bryan on 2006-09-18
*thanks, kurt`... i sometimes forget not everyone's sources.list is 1gb.  ;-)*

---

