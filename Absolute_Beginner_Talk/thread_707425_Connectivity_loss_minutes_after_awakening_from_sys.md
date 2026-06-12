---
title: "Connectivity loss minutes after awakening from system suspend with Gutsy Gibbon"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by sonnychee on 2008-02-25
Hey Guys,

This is a peculiar issue.  After awakening a few minutes from suspend, I will lose Internet connectivity.  The connectivity loss isn't immediate but takes a few minutes before manifesting itself.  Is there a way to repair / reinitialize the ethernet adapter?

I'm running Gutsy Gibbon on VMPlayer.

Sonny.

---

### Post by jbrown96 on 2008-02-26
Here are a few commands that you can try (and I'm sure others could give better ones)

```
sudo /etc/init.d/networking restart
```
Completely restarts networking

```
sudo /etc/init.d/dbus restart
```
Restarts all of Dbus. Probably overkill but it seems to fix the problem more often than the previous command. This does cause some strange behavior on my laptop: the battery icon disappears but the battery state can still be viewed by clicking on the empty space and Nautilus (file browser) opens to my home folder.

```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
```
Commands that restart networking for a particular interface. Change eth1 to your card (ubuntu usually chooses eth0 as the ethernet card and eth1 as wireless).

```
ifconfig
```
Gives info on all network interfaces: MAC address, IP address (if available), options and settings for your cards, etc. 

It might be helpful to also check the system logs and try to see what happens when the connection is lost.

---

### Post by sonnychee on 2008-03-02
Thanks jbrown96, that did the trick!

Sonny.

---

