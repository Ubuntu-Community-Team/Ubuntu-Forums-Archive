---
title: "Setting donut world in freeciv"
date: 2013-06-27
forum: Any Other OS
---

### Post by houseworkshy on 2013-06-27
I've recently changed operating systems and now use the mint based on the latest lts version of Ubuntu duel booting with Debian wheezy, both on xfce.  Formerly I used Ubuntu 10.04 lts with gnome2.  I'm posting here because I can't find the info elsewhere.  Formerly I was able to set topology to a donut ( which is how they spell it ) world isometric before starting a single player game of freeciv.
Searching on the free civ website, forums and wiki finds that it is still available as a servor option [http://freeciv.wikia.com/wiki/Server_options#topology_-_Map_topology_index](http://freeciv.wikia.com/wiki/Server_options#topology_-_Map_topology_index)  yet I can't get at it.  Going into the freeciv servor and using it's built in help I find topology options but the help only tells me how to set the four basic ones, not the others.  Does anyone know how this is done or if it still can be.
A second reason for asking here it that the last time I used the game was in Ubuntu 10.04lts so I wondered if this behaviour change was also the case in Ubuntu now, the mint I now use is the one based on ubuntu 12.04 so it's possible, works in gnome but not xfce perhaps?  Can't find this out directly as gnome fallback is too heavy for my system.

---

### Post by baldiniebaldini on 2014-01-17
To make a toroidal world, the setting is:
```
/set topology WRAPX|WRAPY|ISO
```
However if you play the [Greatturn]("http://civland.org/greatturn/") version of Freeciv, all the settings are already in place so you'll only have to connect to the multiplayer server. (usually there are about 20-30 players there).

---

### Post by lisati on 2014-01-18
*Thread moved to **Other OS/Distro Support**.*

---

