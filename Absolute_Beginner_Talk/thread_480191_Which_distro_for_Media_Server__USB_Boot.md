---
title: "Which distro for Media Server / USB Boot?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by dsewell on 2007-06-21
Hi,

I want to set-up a Linux machine as a low-power media server.  Function and spec as follows:

Machine:
* Epia SP8000, 512mb RAM (fanless, low power)
* 500gb HDD (for data)
* 2gb USB flash (for boot)
* No keyboard, mouse, or VDU once configured

Function:
* Media server
* Back-up
* Torrant
* Web administration
* Power Management (wish to spin-drives down, etc... to reduce power)
* Back-up
* Bomb-proof / solid

I have tried the following distributions with brief comments against each.  All of them booted from USB.
* FreeNAS -- could not mount HDD, seemed unstable
* NASLite -- Rock solid.  Good performance, but no power management
* Linux Puppy -- Small, easy to use, but I couldnt get SAMBA working (I think this was me being a Linux newbie, not the OS)
* ClarkConnect -- Great OS, good web interface, secure, but very slow on my system

So, as I am a newbie, and have read that Ubuntu is a great OS I thought I'd give it a try.  Question is, should I use the Desktop or Server (or other) distribution to perform the above functions?

I have read that desktop can be USB booted.  Not sure about the Server.

I guess I will also need to install software for the following to get the functionality I need:  Torrent; SAMBA; WebMin

Any recomendations before I download and start to play?

Cheers,

Dean

---

### Post by atria on 2007-06-21
I have never tried those distributions that you mentioned so i can't give you any comments regarding them.

Depending on whether you need a GUI for your bittorrent client, the server edition (which does not include the Xserver/gui) should work just fine as long as you know linux commandline.

Samba is included in ubuntu as a software package, just install it with aptitude or synaptic.

Regarding stability, both my ubuntu installations haven't crashed on me before, so i'd say the stability is there.

Finally, instead of using those uncommon distributions, why not give CentOS a try since you're going to use it as a server?

---

