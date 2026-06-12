---
title: "CrunchBang help..."
date: 2011-05-30
forum: Any Other OS
---

### Post by galacticaboy on 2011-05-30
I have tried in the #! forums and nothing so I shall try here. I am wanting to add a PPA so I can test out the new music player from Elementary called BeatBox. The PPA is ppa:sgringwe/beatbox is there a way I can add a PPA on CrunchBang? sudo apt-add-repository does not work on CrunchBang and I cannot find a .deb file, I need the repository so I can get the dependencies with BeatBox.

---

### Post by andymorton on 2011-05-30
You can add the ppa to the /etc/apt/sources.list and then sudo apt-get update, then sudo apt-get install <package>

andy

---

### Post by snowpine on 2011-05-30
PPAs are for Ubuntu and CrunchBang is based on Debian.

Better to get the source code here, I think: [https://code.launchpad.net/beat-box](https://code.launchpad.net/beat-box)

---

### Post by kerry_s on 2011-05-30
or move to lubuntu if you want to stay with ubuntu based & still be lite.
[http://lubuntu.net/](http://lubuntu.net/)

they also have there own os based on ubuntu.
[http://elementaryos.org/](http://elementaryos.org/)

---

### Post by screaminj3sus on 2011-05-30
Addind ppa's on debian sometimes works but its not a great idea. PPA's are designed for ubuntu.

And that ppa is pretty broken even on ubuntu, its missing some needed packages to install beatbox and you have to add the elementary desktop ppa to get them.

---

