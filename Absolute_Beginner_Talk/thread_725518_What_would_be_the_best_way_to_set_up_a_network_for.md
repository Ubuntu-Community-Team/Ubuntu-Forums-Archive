---
title: "What would be the best way to set up a network for 2 or more Xubuntu machines?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-15
I have a machine in my room running Xubuntu 7.10. My little brother also has a machine in his room running Xubuntu 7.10. The router is in my room, I am directly plugged in, and I have a cat5 cable running through a wall into his room so that he is directly plugged into the router. I will eventually be having another machine running Xubuntu 7.10 running upstairs in my brother's room with a wireless connection to our router. 

What would be the best way to set up a network between all of us, so that we may send and receive files to one another much like Network Neighborhood in Windows XP? Eventually, I would like to have a 250gb sata drive used as a server for data storage. I searched around the forum, and I searched around google and couldn't seem to find what I was looking for. I also, would like this to not be gnome dependant. I'm slowly trying to build a Xubuntu install that runs entirely off of xfce packages and will be able to fully get rid of Gnome. (Off the subject, but does anyone know a web browser that doesn't need Gnome packages to run?)

I did start to read a thread here:

[http://ubuntuforums.org/showthread.php?t=250332](http://ubuntuforums.org/showthread.php?t=250332)

Which led me to a thread here:

[http://ubuntuforums.org/showthread.php?t=128873](http://ubuntuforums.org/showthread.php?t=128873)

I got stumped at the second step, but I'm starting to beleive this was meant for people who had already followed some steps I wasn't aware of.

---

### Post by mssever on 2008-03-15
NFS is the standard *NIX way to do this.

---

### Post by joshrobinson on 2008-03-15
your gona want to use samba
this is windows networking, which would be your best bet, its easy, and if you have windows computers in the house they can also share files around

they may have some slight gnome dependencies im not sure on that, but this will allow you to set up a workgroup, and allow you to share files between the networks

just open your package manager, i guess synaptic is still in xubuntu? search for samba and install

---

### Post by PapaNerd on 2008-03-15
General comments not related to the xubuntu configuration:
1. If the three machines all have Gigabit ethernet cards, faster file transfers will be achieved on wired vs. wireless connections, but you'll need a small (at least 4-port) Gigabit switchlet (one port to the router and one to each machine).
2. Be sure you use Cat5e cable that says either "plenum" or "riser rated" on them, otherwise they may not meet local fire codes (and invalidate an insurance claim if there were a fire, even if those wires are not to blame).

---

### Post by Mogurijin on 2008-03-15
I don't know about dependencies and stuff, but you could check out Ice Weasel.

---

### Post by mssever on 2008-03-15
> **joshrobinson said:**
> your gona want to use samba

NFS vs. Samba:

NFS is designed for *NIX computers (including Linux). It preserves file permissions, and in general acts like a *NIX filesystem should act. If you have an all *NIX network, NFS is your best bet. There's also a newer version of NFS (I think it's called NFS4).

Samba is an open source implementation of Windows networking. As such, it doesn't support permissions, or symlinks, or a lot of other stuff. Samba is only a good option if you need to be compatible with machines that can't use NFS (such as Windows).

Bonus: NFS is a lot easier to configure than Samba.

EDIT: Neither NFS nor Samba has anything to do with Gnome.

> **Mogurijin said:**
> I don't know about dependencies and stuff, but you could check out Ice Weasel.
Ice Weasel is Debian's version of Firefox. It has nothing to do with file sharing.

---

### Post by whoscheesemine on 2008-03-15
I read somewhere the Samba does not work on Xubuntu, I'm going to give NFS a shot, thanks a lot I'll post back with results.

---

### Post by whoscheesemine on 2008-03-15
[QUOTE=whoscheesemine;4522913](Off the subject, but does anyone know a web browser that doesn't need Gnome packages to run?)

I beleive he was refurring to that when he mentioned Ice Weasle...

---

### Post by joshrobinson on 2008-03-15
> **mssever said:**
> 


Ice Weasel is Debian's version of Firefox. It has nothing to do with file sharing.


the op also asked for a browser that had no gnome dependencies, thats why ice weasel was mentioned

as for the whole samba nfs thing, i assumed a windows computer was going to be on the network too, but it might not be the case

---

### Post by mssever on 2008-03-15
> **whoscheesemine said:**
> I read somewhere the Samba does not work on Xubuntu, I'm going to give NFS a shot, thanks a lot I'll post back with results.

Maybe whoever wrote that was referring to accessing Samba from Nautilus vs. Thunar. If you mount a Samba share, then it works with anything. But that takes more work to configure, and you're still better off with NFS.

---

