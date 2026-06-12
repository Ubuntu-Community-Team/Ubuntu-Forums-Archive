---
title: "[SOLVED] Synaptic download problem"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Gyzome on 2008-03-14
Hello, I'm a new user to Ubuntu and I have a download problem with Synaptic. It refuses to download after 3 files of each zero bytes. When I installed it first, everything was alright for a few hours, but suddenly it stopped to respond. I reinstalled Ubuntu but the problem persisted. On the LiveCD there were no problems. And with Firefox there's no problem either, I'm using Firefox right now, right here. I had some problems however first, it seemed to lock up with IPv6. As soon as I disabled it, it worked. I changed the following things:
- Disabled IPv6 in Firefox through about:config
- Put a file "bad_list" containing the line "alias-pf-10 off" in "/etc/modprobe.d/" to try to disable IPv6 for everything.

I have a wired connection in Roam Mode.

A picture of Synaptic attempting to download something:
[IMG]http://www.freewebs.com/gyzome/screenshot2.jpg[/IMG]
I stretched the window so you could see everything clearly.
After this it stops, it refuses to download anything. :(
And this is also the same for updating.
And I always get a message that the file is unconfirmed or something alike.

---

### Post by plucky on 2008-03-14
Gyzome,

Disable your CD rom as a Source in **System > Administration > Software sources** or
```
gksudo gedit /etc/apt/sources.list
``` and put a **#** in front of the line that looks like >  deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

and then open a terminal and ```
sudo apt-get update
sudo apt-get upgrade
```

Good luck

---

### Post by Gyzome on 2008-03-15
Hmm... It stops downloading from a cd, but still... No connection with the Ubuntu servers...
I tried this: **System>Administration>Synaptic Package Manager>Settings>Repositories>Download From: Other...>Select Best Server**
It starts to ping and download from servers, then it selects a mirror very close to me, and then I can use Synaptic... For a while... After 5 minutes or so, it locks up again.
Installing .deb packages also doesn't work. For example I tried to install AcetoneISO but the installation required 10 extra packages, so it starts to download but it never gets anywhere, it downloads nothing. Please can someone help me? I'm really desperate!!

---

### Post by handy on 2008-03-15
> **Gyzome said:**
> Hmm... It stops downloading from a cd, but still... No connection with the Ubuntu servers...
I tried this: **System>Administration>Synaptic Package Manager>Settings>Repositories>Download From: Other...>Select Best Server**
It starts to ping and download from servers, then it selects a mirror very close to me, and then I can use Synaptic... For a while... After 5 minutes or so, it locks up again.
Installing .deb packages also doesn't work. For example I tried to install AcetoneISO but the installation required 10 extra packages, so it starts to download but it never gets anywhere, it downloads nothing. Please can someone help me? I'm really desperate!!

I don't know, but there is a slim chance that stabilizing you DNS addresses may help, it can't hurt.

Have a look at the ***The Case of the Disappearing DNS's*** section of [***_this how-to_***]("http://ubuntuforums.org/showthread.php?t=282034")?

---

### Post by plucky on 2008-03-15
Gyzome,

1)Can you copy and paste ```
cat /etc/apt/sources.list
``` so that we can see it.

2)Open a terminal and ```
sudo apt-get update
sudo apt-get upgrade
``` copy and paste any output

3) Does the system hang or just the package manager?

4)Can you download files under Firefox?

5)Try the main server

6)What else have you tried? Running out of ideas here!!!

---

### Post by Gyzome on 2008-03-16
Thx Handy. The DNS switch really helped! For now...
Btw Plucky, I don't mind if your solution helped or not, you _helped_, and that's important to me. Although a working solution comes more in "***Handy***"... :KS

---

