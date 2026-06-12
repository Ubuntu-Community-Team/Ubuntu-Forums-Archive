---
title: "Azureus doesn't download"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by carbonrodney on 2007-05-22
Hello,

Azureus works fine in Windows, but it doesn't in Ubuntu: it starts up, but never has positive download speeds.
NAT always had the green light (and still does). Without changing any settings the torrents wouldn't download more than about 2-4kbps (despite there being good ratios etc.). I changed transfer options to what AzureusWiki  recommended and ignore rules to 'happy to share'. And now all the torrents are 0kbps up and down.

What's going on???

---

### Post by Ferrat on 2007-05-22
First of, why Azureus? drains your comp of so much since it's java based, download wine, install that, then download utorrent, much like Azureus in look and feel, mostly the same functions but much more stable and run on like 1% of what Azureus takes from your system ;)

---

### Post by deadgobby on 2007-05-22
I have no problems with Az. There is a different BT's that can. Like 
[http://deluge-torrent.org/](http://deluge-torrent.org/)
 I installed AZ through Automatix and use it some times. However I am really liking Deluge.
GObby

---

### Post by richaoj on 2007-05-22
here is how i configured azureus to work with ubuntu --

i downloaded firestarter as a gui to configure iptables . . . manually opened up whatever port azureus was using . . . (i recommend not using 6881 or anything around there -- most isps now try to slow down the usual bittorent ports).

i set on my router to have the ubuntu pc have a static ip, manually configured the network connection on the ubuntu pc to have that static ip, and set port forwarding on the router to forward whatever azureus port i choses to the ubuntu pc's static ip.  

i turned of the Upnp plugin in azureus--it seemed to screw things up.

also be sure to limit your upload rate . . . if you don't your dl's will suffer on speed.

another thing that i have done b/c my isp tries to stop my from downloading via torrents is to use encrypted connections (an option in azureus).

---

### Post by irish_flu on 2007-05-22
Perhaps you are accessing the internet through a router with a firewall, and while you've opened the ports for your windows machine, you haven't for your Ubuntu machine?

---

### Post by carbonrodney on 2007-05-24
It's not a firewall problem. As I said, it began to download at 2.5kbps or something upsettingly low.

Although it is avoiding the problem, and not solving it... I am now using another client: KTorrent. I do not like the KDE interface and I have found many KDE based programs to run badly, but this one is awesome. It is simple and doesn't try to do anything you didn't ask for (and screw up in doing so -I'm looking at _you_, Azureus)

---

### Post by senses3 on 2007-10-07
ktorrent runs great in gnome, for a while.  just don't run it in kde or you will get this horrible bar that overlays your original gnome bar.

---

### Post by pierrot on 2007-10-07
Hello!
My problem with "Azureus" is not exacly the same - one time download with 1-2Mb next time - with 0. I could not found the solution - in Win Vista  with uTorrent i reach 4 Mb all the time, and i will try some other program.. Like u say..

p.s. Excuse my mistake, writing this - haven`t practice english long time ago...:lolflag:

---

